---
layout: post
title: "De VMware a Proxmox: Anatomía de una Migración con 1 Millón de Fotos, LXC y TurnKey"
date: 2026-03-30 23:45:00 +0100
categories: [Homelab, Arquitectura de Sistemas]
tags: [Proxmox, VMware, LXC, TurnKey, Immich, KVM, Bind Mounts, OpenVino]
---

Todo administrador de sistemas llega a un punto de inflexión donde lanzar más hardware al problema deja de ser una opción viable. Mi muro de hormigón particular tenía la forma de **1 millón de fotografías**, un servidor basado en un procesador **Intel i5-6500t (45W) con 32GB de RAM**, y el despliegue de **Immich**, una galería open-source que hace un uso intensivo de Machine Learning.

Lo que empezó como un intento de optimizar **VMware ESXi**, terminó en una reestructuración completa de mi arquitectura hacia **Proxmox VE**, abandonando las pesadas máquinas virtuales (VMs) en favor de contenedores Linux (LXC) y plantillas TurnKey. Esta es la bitácora técnica de esa migración y las lecciones aprendidas sobre gestión de recursos.

## La Arquitectura ESXi: El Infierno del Overhead

Mi setup inicial en ESXi parecía la aproximación clásica y correcta para un entorno empresarial tradicional. Mi almacenamiento de 35TB en discos HDD (gama profesional) estaba gestionado por una VM corriendo OpenMediaVault (OMV). Por otro lado, tenía una VM con Ubuntu donde corría el stack de Docker con Immich.

El flujo de datos era el siguiente: OMV exponía un recurso NFS que la VM de Ubuntu montaba a través del vSwitch interno de VMware. 

**El desastre técnico:**
Cuando inyecté el millón de imágenes para su procesado (generación de miniaturas, extracción de metadatos, detección facial y clustering), la arquitectura colapsó. El overhead de red (incluso siendo un vSwitch a 10Gbps lógicos) para leer cientos de miles de archivos pequeños simultáneamente ahogó el sistema. 

Sufrí reinicios constantes de los contenedores Docker por desbordamiento de memoria (**OOMKilled**). Intentar hacer un *passthrough* PCIe de la iGPU de Intel para usar OpenVino fue un dolor burocrático. Terminé asignando a la VM de Ubuntu **12GB de RAM y 3 vCPUs** (de las 4 físicas que tiene el i5). Aún con el host al 80% de carga de CPU sostenida, el procesado inicial me llevó **2 agonizantes semanas**.

## Proxmox y el Falso Debate del Hipervisor Tipo 1

Decidí pivotar a Proxmox para testear la eficiencia de los contenedores LXC. La inercia me llevó a replicar mi entorno inicial en 30 minutos: levanté una VM de OMV, le pasé los discos crudos y expuse NFS. Pero me di cuenta de que estaba desperdiciando la verdadera naturaleza de Proxmox.

A nivel de Sistema Operativo, ESXi es un kernel monolítico brutalmente recortado. Proxmox, en cambio, es un **Debian estable completo**, con el kernel modificado para virtualización. Muchos puristas argumentan que por tener un SO tan amplio con paquetería estándar, Proxmox es un hipervisor de Tipo 2. Esto es técnicamente falso: **KVM se ejecuta a nivel *bare-metal*** y aprovecha las extensiones de virtualización por hardware (Intel VT-x) para traducir direcciones sin pasar por la capa de emulación del SO anfitrión (como sí haría VirtualBox).

Ese "Debian base" me dio la clave para rediseñar el almacenamiento.

## Reestructurando los Discos: Ext4 y Bind Mounts

En Proxmox, el almacenamiento se divide lógicamente en bloques (ZFS, LVM-Thin) y archivos (Directorios). 

ZFS es espectacular (RAID nativo, ARC en memoria RAM, protección contra bit-rot), pero exige aproximadamente 1GB de RAM por cada Terabyte de almacenamiento para funcionar de forma óptima. Con 35TB de discos y 32GB de RAM en el host (necesarios para la IA de Immich), ZFS me habría dejado sin memoria. LVM-Thin era otra opción, pero el almacenamiento a nivel de bloque en crudo impide leer el disco fácilmente fuera del clúster.

**La topología de hardware final:**
* **NVMe WD:** Exclusivo para el SO base (Debian/Proxmox).
* **SSD Crucial de 2TB (ext4):** Destinado a alojar los *rootfs* de los contenedores LXC y las bases de datos de las aplicaciones.
* **35TB HDD (ext4):** Montados directamente a nivel de Debian en el host (`/mnt/data`).

En lugar de crear un disco virtual (`.qcow2`) o usar NFS, utilicé **Bind Mounts** en Proxmox. Esto permite "mapear" el directorio `/mnt/data` del host directamente dentro de un contenedor LXC no privilegiado. 
El resultado: **Cero overhead de red**. El LXC lee el disco físico a velocidad nativa del bus SATA. Además, los datos son 100% portables; si el servidor muere, puedo leer los HDD ext4 en cualquier PC Linux.

## La Magia de TurnKey Linux en LXC

Recordando la VM de OMV que levanté... decidí purgarla. Ya no necesitaba un sistema operativo anidado para servir archivos. 

Aquí descubrí el ecosistema de **TurnKey Linux** integrado nativamente en Proxmox. TurnKey proporciona plantillas de contenedores LXC ultra-optimizadas. Desplegué un *File Server* de TurnKey. En lugar de una VM que consume 2GB de RAM estáticos, ahora tengo un LXC que levanta en 3 segundos, pesa unos pocos megabytes en disco y consume apenas decenas de MB de RAM en reposo, sirviendo la misma carpeta física por Samba/NFS a mi red local.

## Optimizando la IA: Immich y Passthrough de GPU

El despliegue de Immich lo realicé usando los *Helper-Scripts* de la comunidad (tteck), que automatizan la creación de un entorno LXC limpio. Bajo el capó, me montó un Debian 13 y aprovisionó el motor de Docker en el SSD rápido de 2TB. (Tuve que iterar una vez y purgar el LXC porque el SSD tenía la tabla de particiones sucia, una operación de borrado y recreación que en Proxmox tardó literalmente 2 minutos).

Aquí es donde los LXC demuestran su superioridad técnica sobre las VMs en entornos de Homelab:

1. **Gestión de CPU (`host` vs genérica):** En lugar de usar la CPU virtualizada `QEMU64` o `x86_64_v4`, configuré el LXC en modo `host`. Esto expone todas las instrucciones nativas del i5-6500t (como AVX2) directamente al contenedor, algo vital para acelerar las rutinas de Machine Learning.
2. **GPU Passthrough a nivel de nodo:** En ESXi, pasar una GPU integrada (iGPU) a una VM requiere aislar el dispositivo PCIe, lidiar con IOMMU groups y cruzar los dedos. En un LXC de Proxmox, dado que comparte el kernel de Debian, solo necesitas instalar los drivers en el host y mapear los *device nodes* (`/dev/dri/renderD128`) dentro de la configuración del contenedor (`/etc/pve/lxc/ID.conf`). Son dos líneas de texto. OpenVino y QuickSync reconocieron la gráfica instantáneamente.

## Conclusión

Migrar de VMware a Proxmox ha sido una lección de arquitectura. He pasado de ahogar mi procesador de 45W moviendo datos por redes virtuales, a exprimir cada ciclo de reloj mediante contenedores que acceden directamente al metal. 

Con un hardware aparentemente modesto pero distribuido inteligentemente (NVMe para SO, SSD para DBs/LXC y HDD para *Cold Data* vía Bind Mounts), he logrado que el mismo stack de software que tumbaba mi ESXi fluya sin esfuerzo. A veces, la solución no es comprar un servidor más grande, sino quitar las capas de emulación que nos separan del hardware.

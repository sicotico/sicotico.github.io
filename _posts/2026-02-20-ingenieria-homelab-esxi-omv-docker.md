---
layout: post
title: "Desplegando ESXi 8, OMV y Docker con detalles"
date: 2026-02-20 11:00:00 +0100
categories: [Tutorial, DevOps]
tags: [Ubuntu, SSL, Networking, ESXi]
---

# Artículo 3: HomeLab

### Introducción

Tras definir la arquitectura lógica, llegó la implementación técnica. Este artículo detalla la configuración de un entorno compuesto por un host **ESXi 8**, un NAS virtualizado con **OpenMediaVault (OMV)** y un servidor de aplicaciones basado en **Ubuntu Server 24.04** con Docker.

### 1. El Hipervisor: ESXi y el desafío de la identidad

En casa lidiamos con dominios `.local` y certificados autofirmados. Tras cambiar el hostname a `esxi.local`, el certificado SSL seguía apuntando a `localhost`. La solución requirió:
1. Regenerar certificados internos: `/sbin/generate-certificates`.
2. Reiniciar servicios de gestión: `hostd` y `vpxa`.
3. Exportar la CA e instalarla en el sistema cliente para eliminar advertencias de seguridad.

### 2. Almacenamiento: Thick vs. Thin y Passthrough

Para el NAS, configuré **Direct Access (Passthrough)**, permitiendo que OMV gestione los discos físicos directamente. En cuanto al aprovisionamiento:
* **NasVirtual:** Utilicé **Thick Provisioning** para garantizar estabilidad en escrituras pesadas.
* **DockerMV:** Opté por **Thin Provisioning** para ahorrar espacio en el SSD, ya que los contenedores crecen de forma variable.

### 3. La Capa de Contenedores: El error de "Ubuntu Minimized"

Mi primer instinto fue usar la versión *Minimized*, pero eliminaba herramientas básicas de diagnóstico (`net-tools`, `ping`) y dificultaba la instalación de `open-vm-tools`. La solución fue la versión estándar de Ubuntu Server con estas claves:
* **NO a LXD:** Evité instalarlo para no añadir complejidad de red innecesaria.
* **Docker-CE oficial:** Instalado desde los repositorios oficiales, evitando las capas de aislamiento de Snap.

### 4. Redes y DNS: El dominio .local

Configuré el stack TCP/IP y el dominio de búsqueda a `local`. Esto, junto a la edición del archivo `hosts` en macOS, permite acceder por nombre (`https://esxi.local`) en lugar de IPs, profesionalizando la experiencia.

### Resumen Técnico

El resultado es un laboratorio robusto con gestión centralizada de VMware, rendimiento nativo en el NAS y un motor de Docker estándar de industria listo para soportar simulaciones en GNS3.

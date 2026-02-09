---
layout: post
title: "Fase 2: Orquestando el Lab. Permisos en OMV, Volúmenes Docker y el reto de GNS3"
date: 2026-02-15 11:00:00 +0100
categories: [Homelab, Networking, Storage]
tags: [OMV, NFS, SMB, GNS3, Portainer]
---

# Artículo 2: HomeLab

## Introducción: Del "Hierro" al Servicio

En los artículos anteriores, definimos la arquitectura (ESXi sobre Proxmox) y resolvimos los problemas de despliegue (certificados SSL y versiones de Ubuntu). Ahora tenemos un hipervisor estable y dos máquinas virtuales (VMs) funcionando: **NasVirtual** (OpenMediaVault) y **DockerMV** (Ubuntu Server).

Pero un servidor encendido no aporta valor por sí mismo. El valor surge cuando los servicios interactúan. En esta "Fase 2", abordaremos la configuración lógica: cómo gestionar los permisos de nuestros datos en OMV, cómo conectar esos datos con nuestros contenedores Docker y cómo preparar el terreno para la joya de la corona del laboratorio de redes: GNS3.

## 1. OpenMediaVault: La estrategia de Permisos y ACLs

Tenemos **NasVirtual** con acceso directo a los discos físicos (Passthrough). Ahora debemos formatearlos y compartirlos. Aquí es donde muchos administradores noveles fallan: la gestión de permisos en Linux.

### El dilema: SMB vs NFS
Para un entorno mixto (Mac, Windows, Linux), la estrategia de "talla única" no funciona. He separado los protocolos según el consumidor:

* **SMB/CIFS (Para Humanos):** Es el protocolo que usaré desde mi Mac y PCs. Requiere autenticación de usuario y contraseña.
* **NFS (Para Máquinas):** Es el protocolo que usará **DockerMV** para guardar datos persistentes. Se basa en confianza por IP, lo cual es más rápido y transparente para los contenedores.

### Configuración de "Shared Folders" y ACLs
En OMV, el orden de los factores sí altera el producto. Mi flujo de trabajo para evitar errores de "Access Denied" es:

1.  **Sistema de Archivos:** Crear los volúmenes (EXT4 o ZFS) sobre los discos físicos.
2.  **Usuarios:** Crear un usuario `docker_user` con UID específico en OMV que coincida con el usuario en la VM de Docker (para evitar problemas de permisos de escritura).
3.  **Carpetas Compartidas:** Crear la estructura lógica (`/media`, `/backups`, `/docker_data`).
4.  **Privilegios (La clave):**
    * Usar la pestaña **Privilegios** para dar acceso Lectura/Escritura a los usuarios SMB.
    * **EVITAR las ACLs** (Access Control Lists) a menos que sea estrictamente necesario. Las ACLs añaden una capa de complejidad sobre los permisos estándar de Linux (Chmod/Chown) que suele causar conflictos si no se dominan.

## 2. Docker: De la Terminal a la Gestión Visual

Nuestra VM **DockerMV** ya corre Docker-CE de forma nativa sobre Ubuntu. Aunque la terminal es potente, para una gestión diaria rápida, necesitamos visibilidad.

### El primer contenedor: Portainer
La primera pieza de software a desplegar será **Portainer**. Nos permite ver visualmente el estado de los contenedores, redes y volúmenes.

```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    portainer/portainer-ce:latest

### Artículo 3: Enfoque "Lecciones Aprendidas" (Troubleshooting)

---
layout: post
title: "De 'Funciona' a 'Producción': 3 Obstáculos invisibles al profesionalizar un Homelab"
date: 2026-03-02 12:00:00 +0100
categories: [Troubleshooting, SysAdmin]
tags: [VMware, Certificados, Seguridad, Linux]
---

## Introducción: Cuando el tutorial se termina

Cualquiera puede instalar un hipervisor siguiendo "Siguiente > Siguiente". Pero la diferencia entre un experimento casero y una infraestructura fiable (aunque sea doméstica) reside en los detalles que surgen el "Día 2".

En el proceso de desplegar mi nueva infraestructura sobre **VMware ESXi 8** con un hardware modesto (i5-6500, 32GB RAM), me encontré con tres barreras técnicas que rara vez se documentan, pero que son críticas para la operabilidad del sistema. Este post disecciona esos problemas y sus soluciones definitivas.

### 1. La crisis de identidad: SSL y el dominio .local

Uno de los mayores dolores de cabeza en entornos locales es la gestión de certificados. Al instalar ESXi, este genera un certificado autofirmado para `localhost`. Sin embargo, al cambiar el nombre del host a `esxi.local` para integrarlo en mi red, los navegadores modernos (Safari, Chromium) bloquearon el acceso.

**El Problema:**
El certificado no coincidía con el nuevo nombre de host, y peor aún, el enlace de descarga de la CA raíz daba un error 404 en la interfaz web.

**La Solución:**
No basta con cambiar el nombre en la interfaz. Fue necesario descender a la consola SSH y forzar la regeneración de la criptografía del host:

```bash
/sbin/generate-certificates
/etc/init.d/hostd restart
/etc/init.d/vpxa restart

```

Tras esto, el servidor web (`rhttpproxy`) sirvió un certificado con el *Common Name* (CN) correcto: `esxi.local`. Finalmente, exporté el certificado manualmente y forcé la confianza en el "Llavero" de macOS, eliminando para siempre la advertencia de "Sitio no seguro".

*Lección:* La identidad de red debe configurarse antes de desplegar servicios, y la confianza SSL es obligatoria para una gestión sin fricción.

### 2. El mito del "Minimalismo": Por qué Ubuntu Minimized falló

Para mi nodo de Docker, la lógica dictaba usar **Ubuntu Server Minimized** para ahorrar recursos. Error.
En un entorno virtualizado bajo ESXi, la versión minimizada se convirtió en una pesadilla operativa.

**El Problema:**
La imagen carecía de paquetes fundamentales como `net-tools` o `iputils-ping`, complicando el diagnóstico de red. Más crítico aún: las dependencias para `open-vm-tools` estaban incompletas, impidiendo que el hipervisor reportara la dirección IP de la VM o ejecutara apagados ordenados.

**La Solución:**
Reinstalar la versión **Standard** de Ubuntu Server 24.04, pero aplicando una limpieza selectiva durante la instalación:

1. **Rechazar LXD:** Para evitar conflictos de bridges de red con Docker.
2. **Rechazar Docker Snap:** Para evitar el aislamiento excesivo y usar los repositorios oficiales.
3. **Instalar herramientas VMware:** `sudo apt install -y open-vm-tools`.

*Lección:* En virtualización, la "observabilidad" (que el host vea al guest) es más importante que ahorrar 100MB de disco.

### 3. Almacenamiento: Passthrough vs. Virtualización

El almacenamiento es el corazón del laboratorio. Con **OpenMediaVault (OMV)**, tuve que decidir entre crear discos virtuales (VMDK) o pasar el hardware directamente.

**La Decisión:**
Opté por configurar **PCI Passthrough** para la controladora SATA. Esto entrega los discos físicos directamente a la VM del NAS.

* **Ventaja:** Si el ESXi muere mañana, puedo sacar los discos, pincharlos en otro PC con Linux y leer mis datos (EXT4/ZFS) sin necesidad de reconstruir datastores VMFS propietarios.
* **Contras:** Se pierde la capacidad de hacer snapshots de los datos del NAS (pero no del sistema operativo del NAS, que reside en un disco virtual aparte).

Para el resto de máquinas (como Docker), utilicé **Thin Provisioning**. Esto permite "sobrevender" el espacio del SSD, vital en un laboratorio donde creamos y destruimos máquinas constantemente.

### Conclusión

Este laboratorio no es solo un servidor de archivos o de aplicaciones; es un entorno de aprendizaje. Resolver la cadena de confianza SSL, entender las dependencias de las VMware Tools y arquitecturar el almacenamiento para la recuperación de desastres son las habilidades reales que se ganan construyéndolo.

---
layout: post
title: "De Synology a Immich: Guía Maestra de Migración con NFS y Aceleración GPU"
date: 2026-02-09 12:00:00 -0000
categories: self-hosting nas
tags: [immich, esxi, nfs, docker, intel-quicksync]
image: /assets/images/posts/portada-immich.png
description: "Aprende a migrar 300GB de fotos, configurar un NFS resiliente y activar el Passthrough de GPU en ESXi para Immich."
---

# Articulo 5: HomeLab

Migrar tu fototeca desde un NAS tradicional a **Immich** es un cambio radical en privacidad y velocidad. Sin embargo, mover +300GB y configurar la IA para que no colapse el sistema requiere precisión técnica. En esta guía detallamos el proceso real de mudanza, optimización de hardware en ESXi y configuración de red resiliente.

## 1. Mudanza masiva de datos con Rsync

Olvídate de arrastrar carpetas desde el explorador de archivos. Para mover TB de fotos entre servidores de forma fiable, **Rsync** es el estándar de oro.

* **Ventajas:** Reanuda copias cortadas, mantiene metadatos EXIF y verifica la integridad de cada archivo.
* **Comando de ejecución:**
  ```bash
  rsync -avPh --inplace /ruta/origen/ usuario@IP_DESTINO::modulo_omv

```

## 2. NFS Resiliente: Evitando bloqueos en Ubuntu

El error más común es realizar un montaje NFS "duro" que bloquea el sistema operativo si el NAS (OMV) se reinicia. Para evitar que tu servidor Ubuntu se quede colgado, configuramos un **montaje suave (soft mount)**.

### Configuración en /etc/fstab

Edita el archivo de montajes en Ubuntu y añade los parámetros de seguridad:

```text
192.168.68.83:/export/fotos /mnt/fotos_nas nfs _netdev,rw,soft,intr,timeo=150,retrans=3,nofail 0 0

```

* **`soft` e `intr**`: Permiten que Ubuntu "desista" si el NAS no responde, evitando que los contenedores Docker se queden en estado zombi.
* **`timeo=150`**: Espera 15 segundos antes de reintentar.
* **`nofail`**: El servidor arrancará aunque el almacenamiento externo no esté disponible.

## 3. Optimizando el Hardware: GPU Passthrough en ESXi

Para que tu **Intel i5-6500T** no sufra con la transcodificación de vídeo, debemos entregarle la GPU integrada (HD 530) directamente a la VM.

### El conflicto de Virtualización Anidada

Un punto crítico en ESXi: **No puedes usar Passthrough PCI y Virtualización Anidada a la vez.**

1. En la configuración de la VM, **desactiva** "Exponer virtualización asistida por hardware al SO invitado".
2. Añade el **Dispositivo PCI** (Intel GPU).
3. **Reserva de Memoria**: Es obligatorio marcar "Reservar toda la memoria invitada" para que el túnel PCI funcione.

### Comparativa de Rendimiento: Procesamiento de 300GB (i5-6500T)

| Tarea | Solo CPU (Fuerza Bruta) | Con GPU Passthrough (QuickSync/OpenVINO) |
| :--- | :--- | :--- |
| **Generación de Thumbnails** | 12-18 horas (PCPU al 100%) | 2-4 horas (PCPU al 30%) |
| **Transcodificación de Vídeo** | Lenta, saltos en la VM | Fluida, aceleración dedicada |
| **Reconocimiento Facial** | Bloquea la interfaz de usuario | Transparente, en segundo plano |
| **Temperatura del Host** | Alta (>75°C) | Moderada (~55°C) |


## 4. IA y Estabilidad: Solución al error SIGKILL (Out of Memory)

Si ves el error `Worker was sent SIGKILL! Perhaps out of memory?`, la IA de Immich está intentando cargar demasiados modelos simultáneamente.

### Ajuste de Model Cache

Incluso con 10GB de RAM, la carga de modelos de caras (Buffalo_L) y búsqueda (CLIP) puede agotar los recursos. En la interfaz web de Immich:

* **Max Models**: Cámbialo a **1**.
* Esto obliga a la IA a procesar un modelo por vez, liberando RAM antes de cargar el siguiente. Es la clave para la estabilidad en bibliotecas grandes.

## 5. Verificación de rendimiento

Una vez configurado, utiliza estas herramientas en la terminal para confirmar que el hardware trabaja:

1. **`intel_gpu_top`**: Verifica que el motor de video está activo (QuickSync trabajando).
2. **`df -h`**: Confirma que el recurso NFS de 10TB está montado.
3. **`docker stats`**: Vigila el consumo de memoria de los contenedores.

## Solución de Problemas (Troubleshooting)

### La VM no arranca tras añadir la GPU
**Error:** "Nested hardware assisted virtualization is not supported with a PCI passthrough device."
**Solución:** Debes editar la configuración de la CPU de la VM en ESXi y desmarcar la casilla de "Virtualización asistida por hardware". No se pueden tener ambas funciones activas simultáneamente.

### Immich Server no conecta con la IA
**Error:** `Machine learning request failed: fetch failed` o `SIGKILL`.
**Solución:** 1. Revisa que el contenedor `immich_machine_learning` tenga acceso a la GPU (`ls /dev/dri` dentro del contenedor).
2. Reduce el **Max Models** a 1 en la configuración web. El i5-6500T tiene potencia, pero la RAM compartida es un recurso finito.

### Ubuntu se congela al reiniciar el NAS
**Error:** El sistema no responde y los contenedores entran en estado `Dead`.
**Solución:** Asegúrate de usar el parámetro `soft` en el montaje NFS de `/etc/fstab`. Esto permite que el kernel de Ubuntu ignore el error de disco tras 15 segundos en lugar de esperar indefinidamente.

## Conclusión

Migrar a Immich no es solo copiar archivos; es diseñar un ecosistema eficiente. Al combinar la robustez de **NFS resiliente**, el **Passthrough de GPU** y la gestión inteligente de la **memoria de IA**, transformas un hardware veterano en un centro de datos fotográfico de alto rendimiento.

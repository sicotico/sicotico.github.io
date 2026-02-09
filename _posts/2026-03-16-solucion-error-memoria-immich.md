---
layout: post
title: "Immich: Diagnóstico y Resolución del error 'Machine Learning Unhealthy' en Entornos Virtualizados"
date: 2026-03-16
categories: [Self-Hosting, Docker]
tags: [Immich, ESXi, Intel-OpenVINO, DevOps, Troubleshooting]
description: "Guía técnica para solucionar cierres por falta de memoria (OOM) y optimizar la aceleración por hardware en Immich bajo VMware ESXi."
---

# Articulo 6: Homelab

En el despliegue de soluciones de auto-hospedaje como **Immich**, la estabilidad del motor de Machine Learning (ML) es crítica. Un síntoma común en servidores domésticos es el estado `unhealthy` del contenedor de IA, acompañado de errores de red tipo `fetch failed`. Estos errores impiden que funciones clave como la búsqueda inteligente, el reconocimiento facial y el OCR funcionen correctamente.

Este artículo técnico analiza las causas raíz de estos fallos, centrándose en el error de "Worker SIGKILL" y la optimización para hardware específico como el **Intel Core i5-6500T** bajo **VMware ESXi**.

---

![Diagrama de flujo de datos y error de memoria en Immich](/assets/img/diagrama-immich.png)
*Figura 1: Arquitectura de procesamiento asíncrono y el cuello de botella en el motor de ML.*

## 1. Análisis de la Causa Raíz: El "OOM Killer" y sus Implicaciones

Cuando el contenedor `immich_machine_learning` muestra un estado de salud fallido (`unhealthy`), el primer paso es auditar los logs internos para comprender el comportamiento:

```bash
docker logs immich_machine_learning --tail 50
```

La aparición recurrente de la línea `ERROR Worker (pid:XXXX) was sent SIGKILL! Perhaps out of memory?` es la señal inequívoca de un evento **Out Of Memory (OOM)**. En configuraciones Docker por defecto, los límites de recursos pueden ser insuficientes. Al intentar cargar simultáneamente modelos de visión pesados como `ViT-B-32` (Smart Search), `buffalo_l` (Reconocimiento Facial) y `PP-OCRv5` (Texto), el proceso excede la asignación de memoria RAM y el kernel de Linux lo termina forzosamente para proteger la integridad del sistema host.

Este ciclo de muerte y reinicio es lo que lleva al estado `unhealthy` y a los errores de `fetch failed` reportados por otros servicios de Immich que intentan comunicarse con el motor de ML.

-----

## 2\. Implementación de Soluciones: Optimización de Docker Compose y ESXi

Para procesadores con iGPU Intel (como el **i5-6500T**), es imperativo usar la imagen optimizada para **OpenVINO**. Esta optimización mejora el rendimiento, pero requiere un manejo de memoria más generoso.

### 2.1 Ajuste de Límites de Recursos en Docker Compose

Modifica tu `docker-compose.yml` para reflejar límites realistas. Para un flujo de trabajo estable con todos los modelos de ML activados (incluyendo OCR), se recomienda un mínimo de **6GB** de límite de memoria para el servicio de Machine Learning.

```yaml
  immich-machine-learning:
    container_name: immich_machine_learning
    image: ghcr.io/immich-app/immich-machine-learning:release-openvino
    extends:
      file: hwaccel.ml.yml
      service: openvino
    deploy:
      resources:
        limits:
          cpus: '2.0'
          memory: 6144M  # Incremento estratégico de memoria para estabilidad
    devices:
      - /dev/dri:/dev/dri # Mapeo del dispositivo DRI para acceso a la iGPU
    restart: always
```

### 2.2 Consideraciones de Virtualización en VMware ESXi

Correr Immich sobre una VM en **VMware ESXi** introduce una capa de abstracción que puede impactar negativamente el rendimiento de la IA si no se configura correctamente. El i5-6500T con su **Intel HD Graphics 530** es una iGPU, y su correcta passthrough es vital.

#### 2.2.1 Configuración de PCI Passthrough para la iGPU

Para que `/dev/dri` dentro del contenedor de Immich pueda interactuar directamente con la iGPU Intel HD 530 de tu 6500T, debes habilitar el Passthrough:

1.  **Habilitar Passthrough en ESXi:**
    * Conéctate a tu host ESXi vía SSH o la Interfaz de Usuario Web (UI).
    * Navega a **Host \> Manage \> Hardware \> PCI Devices**.
    * Busca el dispositivo **Intel Corporation HD Graphics 530** y asegúrate de que su estado esté marcado como **"Toggle passthrough"**. Actívalo si no lo está.
    * **Importante:** Después de cambiar el estado de Passthrough de un dispositivo PCI, debes **reiniciar el host ESXi** para que los cambios surtan efecto.
2.  **Asignar el Dispositivo PCI a la VM:**
    * Apaga completamente la Máquina Virtual de Immich.
    * Edita la configuración de la VM (Edit Settings).
    * Haz clic en **"Add other device"** y selecciona **"PCI Device"**.
    * En el desplegable, elige la **Intel HD Graphics 530**.

#### 2.2.2 Reserva de Memoria RAM en la VM

Las operaciones de IA son extremadamente sensibles a la latencia y al *swapping* de memoria. El *memory ballooning* de VMware puede causar un rendimiento catastrófico.

  * **Acción:** En la configuración de la VM (Edit Settings), bajo la sección **"Memory"**, marca la opción **"Reserve all guest memory (All locked)"**. Esto garantiza que toda la RAM asignada a la VM sea memoria física dedicada y no esté sujeta a desbordamientos al disco del host.

#### 2.2.3 Ajuste de Memoria de Vídeo de la VM

A pesar del Passthrough, la VM aún necesita una asignación mínima de memoria de vídeo virtual para su propio sistema operativo y para facilitar la gestión del dispositivo.

  * **Acción:** En la configuración de hardware de la VM, bajo **"Video Card"**, selecciona **"Specify custom settings"** y asigna al menos **256MB o 512MB** de memoria de vídeo.

-----

## 5\. Verificación y Monitoreo del Sistema

Una vez aplicados todos los cambios y reiniciado el stack de Docker Compose con `docker compose up -d`, es crucial validar que la aceleración por hardware esté operativa y que los servicios se comporten de manera estable.

### 5.1 Verificación de la iGPU y OpenVINO

Dentro de tu VM de Immich (Linux):

1.  **Instala herramientas de Intel GPU:**
    ```bash
    sudo apt update && sudo apt install intel-gpu-tools
    ```
2.  **Monitorea el uso de la GPU:**
    ```bash
    sudo intel_gpu_top
    ```
    Mientras Immich procesa nuevas fotos, deberías observar actividad en las secciones de **Render/3D** o **Video** de esta herramienta. Esto confirma que OpenVINO está utilizando la iGPU y aliviando la carga del CPU. Si no ves actividad, el Passthrough podría no estar funcionando correctamente.

### 5.2 Monitoreo de Consumo de Memoria de Docker

Observa el consumo real de RAM del contenedor de Machine Learning:

```bash
docker stats immich_machine_learning
```
El consumo de memoria (`MEM USAGE / LIMIT`) debería estabilizarse sin acercarse demasiado a los 6GB asignados (6144MiB) durante el escaneado intensivo.

### 5.3 Monitoreo de Colas de Trabajos (Redis)

Immich utiliza Redis para gestionar las colas de trabajos (jobs). Un motor de ML `unhealthy` hará que estas colas se acumulen.

Para monitorear el estado de las colas, puedes acceder a Redis desde tu host (si tienes `redis-cli` instalado) o desde el contenedor de Redis:

1.  **Acceder al contenedor de Redis:**
    ```bash
    docker exec -it immich_redis redis-cli
    ```
2.  **Listar todas las colas:**
    ```bash
    KEYS "bull:*"
    ```
    Verás nombres de colas como `bull:smartSearch:wait`, `bull:asset-face-detection:waiting`, `bull:ocr:waiting`, etc.

3.  **Ver el tamaño de una cola específica (ejemplo SmartSearch):**
    ```bash
    LLEN bull:smartSearch:wait
    ```
    Si el motor de ML está funcionando correctamente, estas colas deberían vaciarse progresivamente. Si los números aumentan constantemente o permanecen muy altos, indica que el motor de ML no está procesando los trabajos.

Aquí tienes una representación visual de cómo se gestionan estas tareas en Immich:

http://googleusercontent.com/image_generation_content/0



-----

## Conclusión

La robustez de Immich en entornos virtualizados depende de una alineación precisa entre la configuración de Docker, la asignación de recursos de la VM en ESXi y la correcta habilitación de la aceleración por hardware. Al ajustar los límites de memoria y asegurar el Passthrough de la iGPU, transformamos un servicio inestable en una solución de gestión de activos digitales fiable y de alto rendimiento.

---

## Troubleshooting Checklist Rápido

Si sigues experimentando problemas, sigue esta lista de verificación:

* **Docker Compose:**
    * `memory: 6144M` asignado en `immich-machine-learning`?
    * `devices: - /dev/dri:/dev/dri` presente en `immich-machine-learning`?
    * Versión de la imagen ML es `release-openvino` (si tienes iGPU Intel)?
    * ¿Todos los servicios en la misma red de Docker (`docker compose ps`)?

* **VMware ESXi (Configuración de la Máquina Virtual):**
    * **Passthrough PCI** de la iGPU Intel HD 530 configurado y asignado a la VM? (Reinicio de ESXi requerido)
    * **"Reserve all guest memory (All locked)"** activado en la VM?
    * **"Video Memory"** de la VM establecida en 256MB o 512MB?

* **Dentro de la VM (Linux):**
    * `docker ps`: `immich_machine_learning` en estado `(healthy)`?
    * `docker logs immich_machine_learning`: ¿No hay errores `SIGKILL`?
    * `sudo intel_gpu_top`: ¿Muestra actividad mientras Immich procesa fotos?
    * `free -m`: ¿Hay suficiente RAM disponible y poco uso de swap?
    * `docker exec -it immich_redis redis-cli`: ¿Las colas (`LLEN bull:*:wait`) se están vaciando?

* **Configuración de Immich (Interfaz Web):**
    * Si tienes recursos muy limitados, considera desactivar el **OCR** en **Settings \> Machine Learning Settings**. Esto libera una cantidad significativa de RAM.

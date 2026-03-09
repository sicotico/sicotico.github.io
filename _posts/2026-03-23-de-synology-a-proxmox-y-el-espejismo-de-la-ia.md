---
layout: post
title: "De Synology a Proxmox y el Espejismo de la IA: Una Reflexión sobre la Eficiencia, el Tiempo y la Tecnología"
date: 2026-03-23
categories: [Self-Hosting, Docker]
tags: [Immich, ESXi, Intel-OpenVINO, DevOps, Troubleshooting]
description: "Guía técnica para solucionar cierres por falta de memoria (OOM) y optimizar la aceleración por hardware en Immich bajo VMware ESXi."
---

Durante los últimos meses me he embarcado en una misión que muchos apasionados de la tecnología conocerán bien: la construcción del servidor doméstico definitivo. Lo que comenzó como una necesidad técnica, ha terminado convirtiéndose en una profunda reflexión sobre el valor del tiempo, la arquitectura de sistemas y el vertiginoso pero caótico mundo de la Inteligencia Artificial.

# Articulo 7: Homelab

## De Synology a Proxmox y el Espejismo de la IA: Una Reflexión sobre la Eficiencia, el Tiempo y la Tecnología

Si lees mi historial, verás que mi camino no ha sido lineal. Pasé de considerar TrueNAS como mi primera opción, a coquetear con Unraid, hasta que finalmente construí un entorno complejo en VMware ESXi con máquinas virtuales corriendo OpenMediaVault (OMV) y Ubuntu con Docker. Sin embargo, hoy mi laboratorio está en pleno apogeo bajo Proxmox, exprimiendo al máximo los contenedores LXC.

Pero antes de hablar de hipervisores y passthroughs, hablemos de la cruda realidad: **la trampa del hardware frente a la disponibilidad del servicio**.

### El choque de realidad: Hardware brillante vs. Servicios funcionando

Durante años fui un evangelizador de lo simple. A un buen amigo le recomendé: *"Si no sabes de sistemas o no quieres perder el tiempo, paga un Synology. Todo funciona"*. Él me hizo caso. Hoy, él tiene un servidor con un procesador personalizado de AMD que, siendo sinceros, es muy inferior a mi actual configuración (un Intel i5-6500t de bajo consumo pero muy potente, 32GB de RAM, un NVMe para el SO, 2TB de SSD Crucial para VMs y 35TB en discos HDD profesionales).

¿La diferencia? **Él tiene servicios y yo he tenido configuraciones.**

En una quinta parte del tiempo que yo he invertido, él ya tenía su RAID montado y su servidor de vídeo funcionando perfectamente. Mi viejo NAS Synology 120j (con un modesto ARMv7 y 256 MB de RAM) me daba transferencias de 90MB/s por red, y tras 6 años, seguía recibiendo actualizaciones de un software extremadamente maduro y pulido. La integración vertical de un producto con años de experiencia te regala lo más valioso: tiempo.

### La odisea de la IA en local: El desafío de Immich y la migración a Proxmox

Mi viaje se complicó cuando decidí alojar **Immich**, una galería de fotos open-source impulsada por IA (principalmente modelos de Machine Learning para detección de caras, duplicados y metadatos). Mi reto no era menor: procesar un millón de imágenes.

Empecé en VMware. El origen de los datos era un NFS servido por otra VM dentro del mismo host, aprovechando la baja latencia del vSwitch. Pero la configuración estándar fue un desastre frente a mi volumen de datos. Sufrí reinicios constantes de los contenedores por desbordamiento de RAM (*OOMKilled*), uso desmedido de la CPU y tuve que pelear con el *passthrough* de la gráfica integrada (Intel - OpenVino) al contenedor. Llegué a asignar 12GB de RAM y 3 de mis 4 núcleos. Procesar mi biblioteca me llevó dos semanas, lanzando procesos en paralelo que saturaban el sistema al 80%.

Llegados a este punto, replanteé toda mi arquitectura base: había que saltar de VMware ESXi a Proxmox y probar el rendimiento real de los contenedores LXC (Linux Containers).

La soltura ya me acompañaba. En 30 minutos tenía Proxmox corriendo con una VM de OMV y los discos pasados por *passthrough*, igual que en ESXi, pero en una décima parte del tiempo. Pero Proxmox guardaba sorpresas. A diferencia de ESXi, que es un sistema operativo ultrarreducido y capado, Proxmox es un Debian estable modificado maravillosamente para virtualizar con KVM desde el *baremetal*. (Por cierto, es un error clasificar a Proxmox como hipervisor tipo 2 solo porque tiene un SO amplio; KVM traduce instrucciones a nivel de hardware, a diferencia de un VirtualBox).

### Entendiendo la filosofía de Proxmox

Decidí dejar atrás la máquina virtual de OMV que había montado y cambiar de estrategia. Los discos ahora se montan directamente a nivel de Debian (en formato Ext4) y Proxmox los redirige a los diferentes LXC sin privilegios a través de *"bind mounts"*.

Esta revelación fue brutal. Puedo compartir la misma carpeta física con múltiples LXC simultáneamente: uno para que Immich lea las fotos y otro con un servidor de ficheros para subirlas. Y si el host muere, saco el disco Ext4, lo pincho en un PC de sobremesa y mis datos están intactos.

Instalar Immich fue cuestión de usar un *Helper-Script* en la terminal: 10 minutos de proceso y 2 de operación. Hacer un *passthrough* de GPU a un LXC en Proxmox son, literalmente, dos clics en la interfaz web. (Aunque, como en toda bitácora técnica, no faltaron las penurias: un error en la tabla de particiones de un SSD no limpiado me obligó a borrar y rehacer el contenedor, momento en el que me di cuenta de que el script mágico simplemente me había montado un Debian 13 con Docker automatizado).

### El paralelismo con la Inteligencia Artificial: Potencia caótica vs. Madurez

Al escribir esta bitácora, me doy cuenta de que este viaje técnico es un reflejo exacto de lo que estamos viviendo hoy con la Inteligencia Artificial.

Estamos presenciando una guerra titánica entre OpenAI, Anthropic y Google. Probamos herramientas como CursorAI, Antigravity o GitHub Copilot, y la sensación de velocidad es embriagadora.

Sin embargo, hay una diferencia abismal que debemos entender: **la IA actual no tiene, ni de lejos, la madurez de un software consolidado como el de Synology.**

Synology representa un camino determinista, cerrado y altamente optimizado. La IA, por su parte, es un terreno salvaje, no determinista y en constante mutación. Lo que funcionaba hace un año (como los primeros frameworks de agentes) hoy se está fusionando, exige más recursos y requiere nuevos paradigmas de colaboración. Pero lo que le falta de madurez, lo compensa con una **velocidad de avance nunca antes vista en la historia de la tecnología**.

#### Para el usuario administrativo: La regla de la herramienta mínima

Aquí es donde debemos separar los casos de uso. Los usuarios de negocio o administrativos no necesitan (ni deben) entender cómo funciona un agente por debajo, de la misma forma que no necesitan saber si su servidor usa KVM o ESXi. Para ellos, los conceptos básicos no deben ser explicaciones de arquitecturas técnicas.

Su primera herramienta debe ser la mínima viable: un LLM actual (ChatGPT, Claude, Gemini). Estos modelos ya son capaces de realizar tareas complejas y muchos integran agentes nativos de forma transparente. Darles una interfaz sencilla que funcione y les ahorre tiempo es el equivalente a comprar el Synology: pagas (o usas) el servicio para no pelear con la configuración.

#### Para el desarrollador: El peligro de delegar a ciegas

Pero para los que construimos, el riesgo es enorme. Creemos que podemos hacer cosas sin entender lo que hacemos. Hoy puedo usar un agente de IA para programar en **Rust**, un lenguaje en el que jamás he programado.

Con una buena definición de casos de uso, la IA me escupirá un código que, aparentemente, cumple la especificación. Si falla (al ser no determinista), simplemente le pido que lo regenere. Pero cuando por fin funciona y abro el código, los ojos me sangran. Veo estructuras de control extrañas, patrones que no reconozco.

Y aquí surge la pregunta crítica: ¿Cómo valoro que lo creado está bien hecho? ¿Ese código va a generar un desbordamiento de memoria? ¿Va a devorar la CPU y la RAM como si no hubiera un mañana?

El código generado por IA puede funcionar, sí. Pero de la misma forma que mi primera instalación de Immich funcionaba mientras colapsaba mi servidor por falta de optimización, un código de Rust generado por IA y no auditado puede ser una bomba de ineficiencia.

### Conclusión

No se trata de elegir entre la comodidad de un software maduro y la aventura del desarrollo a medida, ni de rechazar la IA porque su código sea imperfecto. Se trata de **criterio**.

El camino desde un modesto NAS ARMv7 hasta un potente nodo de Proxmox con LXC y aceleración gráfica me ha enseñado lo mismo que me está enseñando probar agentes de programación: la tecnología y la IA te pueden dar una velocidad increíble, pero si no entiendes la arquitectura base, los recursos que consumes o las estructuras que validas, terminarás atrapado apagando incendios en lugar de disfrutando del fuego.

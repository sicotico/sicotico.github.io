---
layout: post
title: "La Arquitectura como Equilibrio: Por qué elegí ESXi y Docker sobre Proxmox"
date: 2026-01-08 10:00:00 +0100
categories: [Homelab, Virtualización]
tags: [ESXi, Docker, Arquitectura, OMV]
---

## Introducción: Definiendo la Arquitectura Real

A menudo, en el mundo de TI, caemos en la trampa de definir la "mejor arquitectura" basándonos únicamente en las características técnicas más novedosas. Sin embargo, la arquitectura es el equilibrio entre el conocimiento del equipo y la capacidad de cubrir las necesidades solicitadas.

Tras años desplegando infraestructuras, renové mi *Home Lab* (CPU i5-6500, 32 GB RAM, 8 discos). Aunque **Proxmox VE** era la opción "moderna", elegí **VMware ESXi 8**. Aquí explico por qué el coste de uso no es solo RAM, sino carga cognitiva.

### El Dilema del Hipervisor: La inercia del conocimiento

Proxmox VE 9.x ofrece contenedores LXC nativos, pero mi realidad eran **9 años de experiencia operando VMware**. Adoptar Proxmox implicaba una curva de aprendizaje que habría disparado el "Time-to-Production". Elegir ESXi fue una decisión arquitectónica consciente para minimizar la fricción operativa. El conocimiento previo es un activo que debe amortizarse.

### Aislamiento de Funciones: NAS vs. Docker

Aunque **OpenMediaVault (OMV)** soporta contenedores, apliqué el principio de **Separación de Responsabilidades**. Mi NAS tiene una misión crítica: la integridad de los datos, configurado con *Direct Path I/O* para acceso exclusivo a los discos físicos. 

Mezclar la capa de almacenamiento con la de aplicación es arriesgado. Si mi entorno de Docker colapsa, mi almacenamiento debe seguir funcionando. Por ello, aislé el NAS en su propia VM y dediqué una segunda VM exclusiva para los contenedores.

### La Trampa de la "Eficiencia": Docker vs. LXC vs. LXD

Inicialmente, los contenedores LXC parecían superiores por su bajo consumo. Sin embargo, la **Estandarización** ganó la partida. Docker es el estándar de facto. LXC y LXD introducen complejidades en la gestión de redes y permisos que no compensan el ahorro de RAM en un equipo con 32GB.

Incluso apareció la tentación de activar **LXD** en Ubuntu Server. Fue una distracción de último minuto; al no conocer su operación, quedó relegada a una VM de investigación para mantener el entorno de producción limpio con Docker-CE nativo.

### Conclusión: El bajo coste de uso

El resultado es un entorno donde el mantenimiento es sencillo gracias a los snapshots de ESXi y la estabilidad está garantizada por el aislamiento de funciones. La mejor arquitectura no es la que usa la última tecnología, sino la que te permite dormir tranquilo.

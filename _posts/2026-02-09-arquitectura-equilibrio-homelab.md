---
layout: post
title: "La Arquitectura como Equilibrio: Por qué elegí ESXi y Docker sobre Proxmox"
date: 2026-02-09 10:00:00 +0100
categories: [Homelab, Virtualización]
tags: [ESXi, Docker, Arquitectura, OMV]
---

**Un giro inesperado en el Black Friday**

Todo comenzó como cualquier otro Black Friday: una lista de deseos, un presupuesto ajustado y la firme intención de adquirir un NAS para centralizar mis archivos y respaldos. Mientras navegaba entre ofertas, un anuncio llamó mi atención: una caja JSSON de 8 bahías. En un primer vistazo parecía solo un chasis robusto, pero al leer sus especificaciones descubrí que podía albergar no solo discos duros, sino también una potente placa madre, una tarjeta gráfica y todo lo necesario para montar un PC de escritorio completo.
La decisión fue rápida. En lugar de limitarme a un simple servidor de almacenamiento, opté por transformar esa caja en una máquina versátil que combinaría lo mejor de ambos mundos: la capacidad de un NAS y el rendimiento de un PC de alto nivel. Así, entre luces parpadeantes y el bullicio de las tiendas, mi carrito pasó de contener un modesto NAS a un PC con caja JSSON de 8 bahías, listo para convertirse en el corazón de mi nuevo ecosistema digital.
Y es aquí donde arranca la historia: cómo una compra impulsiva se convirtió en el proyecto más ambicioso de mi año, y cómo cada una de esas ocho bahías encontró su propósito, desde almacenamiento masivo hasta gaming, renderizado y servidores caseros.

---
# Artículo 1: HomeLab

## Introducción: Definiendo la Arquitectura Real

A menudo, en el mundo de TI, caemos en la trampa de definir la "mejor arquitectura" basándonos únicamente en las características técnicas más novedosas. Sin embargo, la arquitectura es el equilibrio entre el conocimiento del equipo y la capacidad de cubrir las necesidades solicitadas.

Tras años desplegando infraestructuras, renové mi *Home Lab* (CPU i5-6500t, 16 GB RAM, 8 discos). Aunque **Proxmox VE** era la opción "moderna", elegí **VMware ESXi 8**. Aquí explico por qué el coste de uso no es solo RAM, sino carga cognitiva.

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

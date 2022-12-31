---
layout: single
title: "Buscando al gorron de la wifi"
date: "2011-12-24"
categories: hardware
---

Consulta ICMP a todos los elementos de la red

`nmap -sP 192.168.1.0/24`

Evitaras que el programa envie un ping antes de realizar el escaneo.

`nmap -sP 192.168.1.0/24 -PO`

Consulta completa a los nodos de la red , puertos "servicios" abiertos y el fingerprint del sistema operativo

`nmap -O 192.168.1.0/24`

La elección de la IP se basa en cuantos octetos varía. En el caso de cualquier hogar el ultimo suele el único en variar y ni siquiera en el rango completo.Para identificar en que situación nos encontramos podemos usar esta chuletilla

- Máscara 255.255.255.0 usad 0/24
- Máscara 255.255.0.0 usad 0/16
- Máscara 255.0.0.0 usad 0/8

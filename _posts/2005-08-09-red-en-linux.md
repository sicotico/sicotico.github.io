---
layout: posts
title: "Red en Linux"
date: "2005-08-09"
categories: linux
---

Sicotico ...

Por si no hicistes bien la instalacion , y configurastes mal la red no te preocupes todo tienes solucion.

Para emepzar entneder que hay que configurar tres cosas en linux la eth0( tarjeta de red ) , las DNS (/etc/resolv.conf) y la puerta de enlace. Porsupuesto esta todo separadito y estructurado xd la tarjeta de red se configura en el archvio /etc/network/interfaces añdir la linea

"iface eth0 inet dhcp" si tienes DHCP o ip automatica ,

sino:

iface eth0 inet static address netmask gateway

bueno pos esto esta listo , cada vez que se inicie la maquina configurar la red automaticamente.

ahora hay que mirar el archivo /etc/resolv.conf y añadir las DNS correspondiente mediante la sintaxis "servername "

ahora ya tenemos la red totalmente configurada.

Si por alguan necesitad necesitamos hacer esto solo para un momento determinado , tnemso como herramientas ifconfig y route , las cuales solo nos configuran la red hasta que reinciemso ya que cogeran los valores de /etc/network/interfaces .

Los pasos son lso siguientes: #ifconfig eth0 up #route add default gw #pico /etc/resolv.conf y a de tener algo aprecido a esto: search nameserver nameserver

---
layout: posts
title: "IP fija en Ubuntu"
date: "2010-11-01"
categories: linux
---

Lo primero son los datos necesarios ,  dejo apuntado los DNS que nunca se cual utilizar

Datos necesarios

- IP
- Máscara de red (Netmask)
- Puerta de enlace(Gateway)
- OpenDNS
    - DNS1 208.67.222.222,
    - DNS2 208.67.220.220
- Google Public DNS
    - DNS1 8.8.8.8
    - DNS2 8.8.4.4

**Nota:** Las dos direcciones DNS esta separas por comas.

_Sistema –> Preferencias –> Conexiones de red_

_Para red de cable:_

_Cableada_ _–> Marcar una red_ _–> Editar_ _–>_ _Ajustes IPv4_ _–> Metodo: Manual_ _–> Direcciones: Añadir_ _–> completar IP , mascara y puerta de enlace_ _–> Servidores DNS_ 8.8.8.8,8.8.4.4 _–> Activar para todos los usuarios_ _–> Aplicar_

_Para red inalámbrica:_

_inalámbrica_ _–> Marcar una red_ _–> Editar_ _–> Inalambrica_ _–> SSID: tu red Wifi_ _–> Modo: Infraestructura_ _–>_ _Ajustes IPv4_ _–> Metodo: Manual_ _–> Direcciones: Añadir_ _–> completar IP , mascara y puerta de enlace_ _–> Servidores DNS_ 8.8.8.8,8.8.4.4 _–> Activar para todos los usuarios_ _–> Aplicar_

La dirección ip debe de estar fuera del rango del servidor DHCP de la red.Normalmente usamos el de router y este es configurable.

Pulsamos en aplicar se desconectar y volverá a conectarse automáticamente en poco segundos , si no es así un reinicio de sera la mejor solución.

## Curiosidades:

\- **OpenDNS:** Es un servidor DNS gratuito y abierto que incluye. [Enlace a Wikipedia](https://es.wikipedia.org/wiki/OpenDNS).

\- **Google Public DNS:** un paso más para gobernar la red [Enlace a Wikipedia.](https://es.wikipedia.org/wiki/Google_Public_DNS)

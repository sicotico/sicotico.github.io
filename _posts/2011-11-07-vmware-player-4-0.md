---
layout: posts
title: "VMWare Player 4.0"
date: "2011-11-07"
categories: vmware
---

Vaya cambio de versión 3.1.4 a 4.0  no se si va más rápido o no  pero han tenido los huevos de hacer mal el paquete de instalación.

En la version 4.0 no instala el ejecutable de configuración de red , y no funcionan las tarjetas tipo "bridge".

Gracias a este [hilo](https://communities.vmware.com/message/1842454 "VMware Player 4.0 no funciona la red en Bridge") del foro de VMware communities te explican como solucionarlo y si todo esta en el paquete original pero al instalarlo no lo copia en el destino y claro no funciona. Tampoco da ningún error.

Solución:

Extrae el paque VMware Player sin instalar

VMware-player-4.0.0-471780.exe /e .vmplayer

En el paquete network.cab localizar el fichero vmnetcfg.exe  y copiarlo a  la ruta donde instalaste el VMware Player 4.0

Fácil sencillo y para toda la familia

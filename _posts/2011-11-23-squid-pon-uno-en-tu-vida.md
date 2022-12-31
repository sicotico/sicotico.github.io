---
layout: single
title: "squid , pon uno en tu vida"
date: "2011-11-23"
categories: linux
---

Había un problema de conectividad y claro un proxy en un servidor siempre es una solución. De corte clásico y elemental. Pero fácil de montar para cualquier ser humano con ganas de leer un poco. La regla elemental que he utilizado , un poco descontrolada pero eficiente para un proxy/cache trasparente

http\_port 8888
visible\_hostname especial
acl All src 0.0.0.0/0.0.0.0
http\_access allow all

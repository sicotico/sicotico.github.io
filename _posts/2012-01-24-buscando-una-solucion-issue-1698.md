---
layout: posts
title: "Buscando una solución Issue 1698"
date: "2012-01-24"
categories: linux hardware
---

Tengo este problema desde el cambio de router

_Issue [1698](https://code.google.com/p/android/issues/detail?id=1698): Wi-fi loses connection with router frequency and doesn't reestablish automatically_

Tiene como workaround el apagar y encender la wifi del dispositivo  , pero es un poco "cutre".

En el último reporte indica que con conexione "G" la conexión no se pierde. Vamos a probarlo !! Comment [](https://code.google.com/p/android/issues/detail?id=1698#c208)208 by [moorgr...@gmail.com](https://code.google.com/u/103214779171497746915/), Jan 11 (6 days ago)

Using Virgin Media SuperHub this happened all the time. I found that by forcing the 802.11 mode down to "Up to 54MBps" I get solid connections. Anything higher (145, 300MBps) results in very short connections that freeze / no connection at all.

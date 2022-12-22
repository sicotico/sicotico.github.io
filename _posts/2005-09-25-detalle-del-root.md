---
layout: post
title: "Detalle del root"
date: "2005-09-25"
categories: linux
---

Sicotico ...

Bueno no se si a mas gente le habrá pasado lo mismo que a mi , en la consola de kde siendo root no me deja abrir ventanas , aplicaciones graficas , devolviendome este error:

Xlib: connection to ":0.0" refused by server Xlib: No protocol specified

kcalc: cannot connect to X server :0.0

para solucionarlo solo hay que ejecutar como usuario

\# xhost +local:root --> Para dar acceso a root solo en localhost

\# xhost -local:root --> deniega le permiso

Esto hay que hacerlo porque que el superusuario no tiene la posibilidad de conectarse al servidor de las X si no las ha iniciado el , asi que mediante xhost lo que hacemos es permitir el acceso al servidor de todos los usuarios locales , mediante una ACL "Accees Contol List".

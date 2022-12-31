---
layout: single
title: "Monitor externo"
date: "2011-07-14"
categories: dev
---

Este caso es solo valido para hardware compatible con la gestión de monitores por los modules nativos del kernel. ATI y Nvidia se ha de utilizar la herramientas propias.

Primero averiguamos el nombre del monitor utilizando

xrandr

Obtenemos una salida parecida esta:

Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 376mm x 301mm
1280x1024      60.0\*+   75.0
1152x864       75.0
1024x768       75.1     70.1     60.0
832x624        74.6
800x600        72.2     75.0     60.3
640x480        72.8     75.0     60.0
720x400        70.1
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
1280x800       60.0\*+
1024x768       60.0
800x600        60.3     56.2
640x480        59.9
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

Se ha detectado el segundo monitor como "VGA1"

Con este comando establecemos la resolución para el monitor externo "VGA1"

xrandr --output VGA1 --mode 1280x1024 --rate 60

Fuente: [ubuntuforums](https://ubuntuforums.org/showthread.php?t=1721927&highlight=force+resolution+external+monitor "Force resolution")

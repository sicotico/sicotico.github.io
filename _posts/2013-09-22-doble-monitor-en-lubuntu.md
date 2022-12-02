---

title: "Doble monitor en Lubuntu"
date: "2013-09-22"
categories: 
  - "sin-categoria"
---

## Doble monitor

Problemas con el Doble monitor en Windows y Linux , el mismo problema para ser exacto , no se detecta la resolución del monitor y asigna por defecto las tres básicas. El monitor es 1080p y esta funcionando a 768p lo cual es una tortura

[![doble_monitor](images/9844002236_700433340c_z.jpg)](https://www.flickr.com/photos/12949201@N08/9844002236/ "doble_monitor por sicotico, en Flickr")

Dispositivos gráficos conectados , en mi caso LVDS es el portátil y VGA1 el monitor externo

Mediante terminal y con la herramienta xrandr configuraremos la resolución del monitor externo y su colocación

Borrar un modo , muy útil si lo has asignado mal

    sudo xrandr --rmmode 1920x1080\_60.0

Obtener los parámetros de refresco para una resolución

    gtf 1920 1080 60.0

Crear un modo (resolución , frecuencia y refrescos de pantalla)

    sudo xrandr --newmode "1920x1080\_60.0" 172.80 1920 2040 2248 2576  1080 1081 1084 1118 -HSync +Vsync

Asignar un modo a uno de los dispositivos conectados

    sudo xrandr --addmode VGA1 1920x1080\_60.0

Habilitar un modo asignado previamente a ese dispositivo

    sudo xrandr --output VGA1 --mode 1920x1080\_60.0

A partir de ahora utilizaremos el ArandR , con las instrucciones de [Lubuntutips](https://www.lubuntutips.com/2012/05/dual-monitors-in-lubuntu.html "Dual monitor  Lubuntu")

Con la herramienta AranrD , un interfaz para mejorar el uso de xrand ,  se guardan todos los cambios en un fichero de Script de shell. He colocado las pantallas como las quiero ver , igualadas por el marco inferior como referencia  y lo en guardado en un el fichero sh. ahora lo edito  y he copiado y pegado el contenido en e mi fichero de script. Así tras asignar la nueva resolución puedo colocar las pantallas como yo quiero.

En este caso cuando se apaga o desconecta el monitor externo el modo 1080 pasa a ser asignado a la salida TV1 , así que se tras crear el modo se puede comentar y no volver a usar.

### Script en Bash de ejemplo para configurar una nueva resolución en el monitor externo (VGA1)

#!/bin/bash

#No es necesario , pero la primera vez sí
echo "borrar modo 1080"
xrandr --rmmode "1920x1080\_60.0"

#No es necesario , pero la primera vez sí
echo "nuevo modo"
xrandr --newmode "1920x1080\_60.0" 172.80 1920 2040 2248 2576  1080 1081 1084 1118 -HSync +Vsync

echo "Asignar resolucio al monitor externo"
xrandr --addmode VGA1 1920x1080\_60.0

echo "Establecer la reoslucion"
xrandr --output VGA1 --mode 1920x1080\_60.0

#Creado con ArandR
echo "ordenar pantaallas"
xrandr --output DP3 --off --output DP2 --off --output DP1 --off --output TV1 --off --output HDMI2 --off --output HDMI1 --off --output LVDS1 --mode 1280x800 --pos 1920x280 --rotate normal --output VGA1 --mode 1920x1080\_60.0 --pos 0x0 --rotate normal

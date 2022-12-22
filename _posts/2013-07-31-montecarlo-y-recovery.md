---
layout: posts
title: "Montecarlo y Recovery"
date: "2013-07-31"
categories: android
---

## Recovery

Esto es lo que queremos ponerle a nuestro Montecarlo.  Esto nos proporciona el acceso al borrado de caches , particionar la SD para instalar aplicaciones en ella , resetear el terminal , arregla los permisos, un largo etcétera de operaciones.

## Requisitos

Instalar los drivers de ZTE Montecarlo, esto se puede hacer la primera vez que enchufas el móvil, es recomendable reiniciar el equipo. Yo no he conseguido que me funcione nuca, así que realizo una actualización de los drivers.

## Pasos

- Conectamos por USB el movil al Pc y dejamos que se instalen los drivers de ZTE
- Reiniciamos el pc (importante)
- Desconectamos el movil y activamos la depuración USB en ajustes->aplicaciones->desarrollo->activamos depuración USB
- Volvemos a conectar el movil
- Ejecutamos el 0\_Install\_CWM\_recovery.bat que hay en la carpeta que hemos descomprimido al principio
- Veremos que el movil se reinicia y se queda un rato en la pantalla que sale "ZTE-Skate", luego debe volver a reiniciarse solo
- Ahora deberemos tener correctamente instalado el Clockworkmod Recovery en nuestro Skate.
- Podemos entrar al recovery encendiendo el móvil y acto seguido dejar pulsado volumen- hasta que el móvil vibre, entonces entrara al recovery.

## Problemas comunes

Los drivers no se instalan correctamente ,  esto se debe que los referentes a almacenamiento son estándar  y los de gestión del dispositivo no.  Así que puedes tener unos drivers sin instalar.

\[flickr\]https://www.flickr.com/photos/12949201@N08/9371231847/\[/flickr\]

Solución:

Descargamos **[\>esto<](https://minus.com/mopTD5NAa/)** (**[Enlace alternativo](https://www.mediafire.com/?8fle7p5s22qycyw)**) y lo descomprimimos donde queramos.

Actualicemos los drivers del dispositivo de nombre Android y con interrogación , en la consola de "Administración de equipos"\\"Administrador de dispositivos

Descomprimimos el fichero y le indicamos al asistente de los drivers la ruta de la carpeta "usb\_driver"

Ahora ya podemos lanzar el instalador del recovery

### Fuentes:

https://www.htcmania.com/showthread.php?t=285880

https://www.htcmania.com/showthread.php?t=361627

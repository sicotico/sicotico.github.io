---
layout: posts
title: "Linux + Android"
date: "2010-11-01"
categories: android
---

Para hacer visible un termina Android en linux es necesario informar un poco al subsitema udev , para que sepa lo que tiene que hacer con el aparato.

Creamos un fichero de reglas udev

sudo vi /etc/udev/rules.d/09-android.rules

En el ponemos

SUBSYSTEM=="usb", ATTR{idVendor}=="22b8", MODE="0666", GROUP="usuario"
SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", MODE="0666", GROUP="usuario"
SUBSYSTEM=="usb", SYSFS{idVendor}=="04e8", MODE="0666", GROUP="usuario"
SUBSYSTEM=="usb", SYSFS{idVendor}=="18d1", MODE="0666", GROUP="usuario"

**Nota:** "usuario" tiene que ser cambiado por un grupo sobre el que tengáis permisos , normalmente en derivados de Debian el grupo es igual al al nombre de usuario.

Reiniciarmos el demonio udev , a mi personalmente me obligo a reiniciar el sistema.

Para verificar que funciona correctamente hay que descargarse y descomprimir el sdk  y ejecutar dentro de la carpeta tools el comando

./adb devices

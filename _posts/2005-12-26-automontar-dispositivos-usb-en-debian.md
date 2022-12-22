---
layout: post
title: "Automontar dispositivos usb en Debian"
date: "2005-12-26"
categories: linux
---

Esto es para vagos , que a mi no me gusta el "mount" arriba abajo todo el dia , esun poco cansino ,y visto k hay un monton de chapuzas de scripts pues mejor dar la opcion oficial de debian.

Instalar usbmount: # apt-get install usbmount

para decirel donde quiero que los monte , edit el fichero usbmount.conf: #pico /etc/usbmount/usbmount.conf

y en la seccion MOUNTPOINTS lo elijo , despues hay que modificar FILESYSTEMS y añadir vfat porque no lo soporta de inicio , ademas yo he cambiado  a MOUNTOPTIONS="sync,noexec,ndev". En la opcion FS\_MOUNTOPTIONS te deja elejir que parametros amayores quieres añadir en cada sistema de ficheros (vfat,ntfs,ext3,ext2) , asi qeu para que no fallen la "ñ" o las tíldes añadiremos -fstype=vfat,nls=iso8859-15

---
layout: post
title: "Personalizar grub"
date: "2005-12-07"
categories: 
  - "sin-categoria"
---

Como estaba aburrido a las 3 de la mañana pues nada dije voy a poner bonito el horrible grub azul , qu epor defecto viene en debian. Lo primero es saber como demonios son las particiones en grub , (hdx,y) donde "x" es NumBios y la "y" NúmParticion . Ejemplo

/dev/hda1 (hd0,0)

/dev/hda2 (hd0,1)

/dev/hda3 (hd0,2)

/dev/hdb1 (hd1,0)

Suficiente para pillarle el truco xD.......

ahora pongamos mas lineas en la pantalla , mas resolución , con solo añadir vga=0x318 en la linea de kernel ya esta solucionado.

Posibles valores del parámetro vga:

<table><tbody><tr><td>&nbsp;</td><td><strong>640x480</strong></td><td valign="top">&nbsp;</td><td><strong>800x600</strong></td><td><strong>1024x768</strong></td><td><strong>1280x1024</strong></td></tr><tr><td><strong>256</strong></td><td>0x301</td><td valign="top">&nbsp;</td><td>0x303</td><td>0x305</td><td>0x307</td></tr><tr><td><strong>32k</strong></td><td>0x310</td><td valign="top">&nbsp;</td><td>0x313</td><td>0x316</td><td>0x319</td></tr><tr><td><strong>64k</strong></td><td>0x311</td><td valign="top">&nbsp;</td><td>0x314</td><td>0x317</td><td>0x31A</td></tr><tr><td><strong>16M</strong></td><td>0x312</td><td valign="top">&nbsp;</td><td>0x315</td><td>0x318</td><td>0x31B</td></tr></tbody></table>

Adornemos un poquito el feo grub , para ello instalamos el paquete grub-splashimages con apt y añadimos esta linea en la posición indicada : #Put static boot stanzas before and/or after AUTOMATIC KERNEL LIST

splashimage (hdx,y)/boot/grub/splashsimages/fista.xmp.gz

\### BEGIN AUTOMATIC KERNELS LIST

en al ruta antes citada se encuentra varias imagenes que podemos poner al grub.

Las imagenes de grub son especiales sus requisitos son formato xmp , máximo 14 colores , resolución 640x480 y comprimidas en gz.

(light significa resaltado))

Si la foto no es lo nuestro podemos cambiar los colores color gree/black light-gree/black --> esta es la conbiancion que a mi me gusta.

Por si se os olvida aquí pongo un ejemplo de como es una entrada para un sistema windows :

title winxp

root (hd0,0) --> varia segun la particion , tal como indico al principio del post makeactive

chainloader +1

y otra para un sistema Linux:

title Debian Sarge

root (hd0,1)

kernel /boot/vmlinuz root=/dev/hda2 ro console=tty0 vga=0x318

initrd /boot/initrd.img

savedefault

boot

Pues esto es to es to es to es todooooooo amigos .....................

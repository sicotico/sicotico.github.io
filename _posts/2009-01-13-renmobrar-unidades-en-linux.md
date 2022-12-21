---
layout: post
title: "Renmobrar unidades en Linux"
date: "2009-01-13"
categories: linux
---

Estoy de organización ,en el server ,y un detalle importante es el punto de montaje de las unidades y su etiqueta.

En este [enlace](https://luispuente.net/2007/07/bug-gnome-mount/) se comenta como elegir la ruta de montaje , siempre que dependa de /media/

Esto no es suficiente ya que en el escritorio aparecerá nombrado con su etiqueta .Para solucionarlo utilizaremos una par de aplicaciones. `sudo apt-get install mtools sudo apt-get install ntfsprogs sudo apt-get install e2fsprogs` Lo primero es identificar el disco duro ,  partimos de la unidad auto montada con el nombre viejo , ahora cambiamos su punto de montaje mediante el [interface de GNOME](https://luispuente.net/2007/07/bug-gnome-mount/) , para este caso el punto de montaje sera "Prueba"

(Acuérdate de desmontarlo y montarlo)

Ahora sabiendo  su punto de montaje identificar cual es nuestro mediante comandas es mucho más sencillo, utilizaremos el comando:

`mount` y obtendremos un salida parecida a esta:

`/dev/sdi1 on /media/Prueba type ext3 (rw,nosuid,nodev,uhelper=hal) /dev/sdf1 on /media/Ejemplo type vFat (rw,nosuid,nodev,uhelper=hal)`

Ya tenemos nuestro disco situado , de tipo ext3 , ahora la re nombramos con e2label

`sudo e2label /dev/sdi1 Prueba`Ext3

Ya tenemos nuestro disco situado , de tipo Fat32 o Fat16 , ahora la re nombramos con mtools `sudo mlabel -i /dev/sdi1 -s ::PruebaFat`

Ya tenemos nuestro disco situado , de tipo Fat32 o Fat16 , ahora la re nombramos con ntfsprogs

`sudo ntfslabel /dev/sdi1 PruebaNFTS`

Listo ya tenmos situados los discos duros y bien nombrados

Fuente: [RenamingUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

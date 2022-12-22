---
layout: posts
title: "optimizar Ext4 con fstab"
date: "2013-12-26"
categories: linux
---

## Optimizar Ext4

![filesystem](images/filesystem.png)

Toca dar un poco de _vidilla_ a esos discos duros que tengo en modo almacenamiento de diógenes. Hay que especificar que esta parametrización la utilizo para discos duro de almacenamiento y el sistema /tmp en RAM. No se debe de utilizar para otros fines.

Un poco de teoría , eso lo tenemos en  la explicación del _man_ del _fstab_  o en [FSTAB](https://wiki.archlinux.org/index.php/Fstab_%28Espa%C3%B1ol%29 "fstab") de ArchLinux. Aquí podemos leer el porque de cada uno de los parámetro que utilizo , y alguno más  que a lo mejor os puede hacer falta.

Los primero es quitar el _defaults_ ,  es un poco de estorbo ya que con _user_ son dos super parámetros, esto sengloban variso y luego colisionan. Yo prefiero ponerlos de uno en uno  cuando sea posible.

Editamos el /etc/fstab

localizamos nuestro dispositivo (mediante UUID , si no hemos sido buenos chicos dejando los comentarios bien puestos)

Esto es como lo tengo ahora (fijaros en el comentario ;) ):

#Cosas1         /dev/sdb1
UUID=a13e4ab5-5979-4451-b093-69af9ae9761d       /media/series   ext4    rw,user,suid,dev,exec,auto,async,noatime,nofail,data=writeback,nobh     0       0

 

Ahora paso a paso ver lo que he puesto para optimizar ext4

rw,user,suid,dev,exec,auto,async,noatime,nofail,data=writeback,nobh     0       0

 

Listado de parámetros utilizados

-  _rw:_ Lectura y escritura
- _user:_ Permite a un usuario  montar el dispositivo
- _suid: _ Ejecuciones con elevaciones de privilegios para los usuarios
- _exec:_ Permite ejecutar binarios
- _auto:_ Se monta automáticamente al inicio y con el parámetro
- _async:_ Escritura asíncrona de datos en el disco
- _noatime:_ No registra modificaciones  en el diario para ficheros y directorios
- _nofail: S_i el dispositivo no existe no emite fallo y continua el proceso
- _data=writeback:_ Especifica escritura rápida para los metadatos , al estilo de XFS
- _nobh: Es necesario habilitar el writeback primero._ Esto no lo entiendo así que os dejo el enlace: [Optimizar Ext4 y Ext3](https://www.pacorabadan.com/?p=557 "Optimizar Ext4 y Ext3")

Ahora actualizaremos el tipo de registro diario a _"writeback"_

tune2fs -o journal\_data\_writeback /dev/sdXX

Ya hemos acabado con los parámetros de montajes , ahora hagamos un poco de "tune" en los sistemas de ficheros.

Esto son tareas más regulares de mantenimiento , todas empiezan igual

**HAY QUE DESMONTAR LOS SISTEMAS DE FICHEROS** ,

después ya ejecutamos los comandos.

e2fsck -f -D /dev/sdXX

## Fuentes:

[Optimizar Ext4 y Ext3](https://www.pacorabadan.com/?p=557 "Optimizar Ext4 y Ext3")

[FSTAB](https://wiki.archlinux.org/index.php/Fstab_%28Espa%C3%B1ol%29 "fstab")

[Optimización de sistemas de archivos ext3 y ext4](https://www.alcancelibre.org/staticpages/index.php/como-optimizar-ext3 "Optimización de sistemas de archivos ext3 y ext4")

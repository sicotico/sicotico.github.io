---
layout: posts
title: "El superblock"
date: "2011-11-06"
categories: linux windows
---

Estos son los primero enlaces que he utilizado tras obtener un maravilloso error de lectura del "magic number" en la partición del sistema.

dumpe2fs: Bad magic number in super-block mientras se intentaba abrir

Un poco complicado de trabajar en ella , así que recopilo información y avanzo que un chroot desde LiveCD vamsoa tener que hacer.

\* [Damaged Superblock](https://www.brunolinux.com/04-The_File_System/Damaged_Superblock.html "Damaged Superblock")

\* [Data recovery technique from corrupted ext2/ext3 filesystem having bad superblock](https://aniraj.blogspot.com/2006/05/data-recovery-technique-from-corrupted.html "Data recovery technique from corrupted ext2/ext3 filesystem having bad superblock")

Lo básico sobre el un superbloque o superblock es la información que contiene. Simplemente alberga datos descriptivos del sistema de ficheros. En este caso el dato que falla es el "magic number" para identificar el sistema de ficheros, geometría, estadísticas y información del 'tunning'. Aun siendo importante el sistema ficheros arranca correctamente ya que no todo el superblock esta corrupto. Este dato es muy importante, normalmente en ext2 , ext3 y ext4 se guarda un backup del superblock disperso por el disco, tienes algo mas información en:

[Understanding unixlinux filesystem superblock](https://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-superblock.html "Entenido el superblock")

Vamos a probar su recuperación , en mi caso he de reiniciar y acceder al FS desde un LiveCD o LiveUSB , de unas de esas copias, ejemplo:

1) Ejecutar "mke2fs -n /dev/sda3" para saber donde asten las copias de seguridad del superblock:

 mke2fs -n /dev/sda3

Respaldo del super bloque guardado en los bloques:

32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, (..)

2) Reintentar un chequeo especificando a e2fsck que use un superblock diferente del 0 (cualquier de los que nos dio mke2fs -n):

 e2fsck -B 4096 -b 32768 /dev/hda6

3) Si finalmente queremos sustituir el superblock por el de backup utilizar la opción "-S" de mke2fs.

Si el método recuperar el superbloque no te funciona, prueba a montar la partición del siguiente modo, ejemplo:

 mount -t ext2 -o ro,errors=recover,errors=continue /dev/sdb1 /mnt

Si esto tampoco funciona, y estás seguro de que el fichero "disk-0.img" contiene un sistema de ficheros, y no una imagen de un disco (que podría tener mas de una partición), entonces tendrás que tirar de alguna aplicación tipo "dd\_rescue" o similar para tratar de recuperar el contenido, un simple 'dd' para empezar a probar:

 dd if=/dev/sdb3 of=/sdb3-backup/image/backup

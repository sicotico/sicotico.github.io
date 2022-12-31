---
layout: single
title: "Mi FileServer"
date: "2011-08-28"
categories: linux
---

Configuración básica de mi maquina virtual comparte ficheros

La base de este equipos es una Ubuntu Server 11.04 , con el perfil de instalación "Servidor Samba". Instala un sistema mínimo y los paquetes de samba , tengo como costumbre actualizar el sistema antes de empezar a hacer nada. Y por si acaso mejoraba algo he puesto las herramientas de "Guest" de mi software de virtualización.

Los primero es genera un fstab con puntos de montaje estáticos , identificamos cada dispositivo por su UUID y le asignamos los permisos y el punto de montaje

$ sudo blkid /dev/sda1
/dev/sda1: UUID="8b6ec432-1f41-49f3-82da-d2abab43fa987" TYPE="ext4"

Por comodidad desde root puedes redirigir la salida a le fichero `fstab`

$ sudo su
 blkid /dev/sda1 >> /etc/fstab

Retocamos el `fstab` con los permisos y los puntos de montaje , fijándonos bien en el parámetro LABEL.

Preparamos los permiso de los recursos a compartir.

- chmod -R
- chown -R user:group

Ahora toca retocar el smb.conf con los recursos que queremos compartir , por supuesto a golpe de vi

 

\[Nombre del recurso\]
comment =
browseable = yes  Marcamos que sea navegable
path = Ruta de la carpeta
writable = no Este valor esta condicionado por los permisos , así que hay que sincronizarlo
public = yes

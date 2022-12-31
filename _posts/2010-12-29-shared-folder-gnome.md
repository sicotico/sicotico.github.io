---
layout: single
title: "Shared Folder GNOME"
date: "2010-12-29"
categories: linux
---

Desde hace varias versiones GNOME posee un sistema para compartir carpetas que se configura de forma automática al iniciarlo la primera vez. Muy al estilo de windows utiliza el botón derecho para compartir un recurso , si falta el paquete de samba el mismo te lo instala.

Antes existía el `smb.conf` y había que dar de lata ahí los recursos a compartir , que de noche me pase leyendo esa mierda de fichero ,  también tenias controlado lo que compartías. Hace un par de minutos me surgió esa duda en mi equipo de casa así que me lance a la búsqueda de la información. Lo primero mirar en el ombligo de uno lanzamos un `find -name samba` para las ruta `/etc` y `/var` , me pongo a leer los de `/var` y me encuentro con `/var/lib/samba` dentro tenemos una carpeta de nombre `usershares` con un fichero por cada recurso que tienes compartido.

Ruta de configuración de las Carpetas Compartidas de GNOME `/var/lib/samba/usershares`

---
layout: post
title: "Formatear en Linux"
date: "2006-10-22"
categories: 
  - "sin-categoria"
---

  
Una curiosidad de como se hacia esto en Linux me llevo a cometer muchos errores , lo malo es que hasta días después no supe que eran errores.

Dije bueno si no se hacerlo por consola uso el asistonto de Gnome

Sistema-->Administración--> Discos

Pero no sirvió de mucho , con esa apariencia muy MacOS X , no me ayudo mucho la verdad , tras acabar de formártela en varios click una facilidad increíble , volqué todos los datos al hdd nuevo y mi sorpresa fue cuatro días mas tarde el cfdisk m detecta la partición como "W95" . Esto si que es un susto hdd de 500GB LaCie nuevo con 390GB ocupado y uno 15gb perdidos por las tablas de asignación de EXT3 con Journalig de datos y metadatos , la seguridad ante todo. Como por ahora todo funciona bien no me he asustado pero he buscado como hacerlo y me ha salido esto en el handbook de Gentoo así que me fio. #mke2fs -j /dev/.... (hay que poner una partición , no unidad)

Apunto tambien actuaciones con el fdisk.

1. sudo fdisk /dev/"Dispositivo"
2. Opción" d" suprimir partición
3. Opción "o" crea una nueva tabla de particiones
4. Opción "n" crea una partición (yo lo hago con el tamaño máximo)
5. Opción "w" guarda cambios
6. #mke2fs -j /dev/"Dispositivo"

Si os veis muy apurados y no os sale algo , podeis usar qtparted como root y luego usar el e2fsck -f-y /dev/"Dispositivo" para verificar el sistema de ficheros o volver formatear con mke2fs -j /dev/"Dispositivo"

---
layout: post
title: "ZTE MonteCarlo modificar la MAC"
date: "2014-01-01"
categories: android
---

## zte montecarlo

Para este proceso necesitas tenerla apuntada anteriormente.

Nota: Este post se escribió tras los comentarios en la entrada  [Skate (ZTE) volver al estado de fábrica](https://luispuente.net/skate-zte-volver-al-estado-de-fabrica/ "Skate (ZTE) volver al estado de fábrica")

### Truco:

\[box type="info"\] Si no la tienes puedes tirar de los logs del DHCP del router donde la puedes obtener.\[/box\]

## Necesitamos modificar un fichero del sistema operativo.

Es necesario ser root o poseer los privilegios en zte montecarlo

### Instrucciones:

- Con la ROM nueva necesitamos ser root  y utilizar una aplicación de explorador de ficheros , yo he utilizado  ES File explorer.
- Para estas aplicaciones debemos de activar su modo root
- Editamos el fichero: _system/etc/nv\_4319.txt_
- Localizamos la linea “macadress=…”
- Modificamos … por  "Nuestra\_MAC"

Fuentes:

[HTC Mania - PainKiller](https://www.htcmania.com/showthread.php?p=3148587#post3148587 "HTCMania Painkiller")

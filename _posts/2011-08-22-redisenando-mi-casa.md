---
layout: posts
title: "Rediseñando mi casa"
date: "2011-08-22"
categories: hardware
---

Ya tengo mi "host" , que cosas se me pegan las expresiones. Toca renovarse , si me he comprado un [iMac](https://support.apple.com/kb/SP588?viewlocale=es_ES "Especificaciones tecnicas") debería aprender a usarlo. Voy hacer el intento de aprender Mac OS X .

El paso esta marcado porque no me funciona el segundo monitor , via HDMI así que algo de ayuda he tenido.

Lo malo es que tengo dos disco externo y formateados en ext4 , sistema de fichero que conozco un poco y sobre todo se recuperar ficheros. He probado Mac-fuse con fuse-ext2 y el rendimiento era realmente malo. La opción que me recomendaron fue convertir los discos a un sistema NAS , pero requería de un nuevo equipo. Como la idea era buena simplemente he levantado una maquina virtual con un Ubuntu Server mínimo con samba.

Modificando el fstab para que monte los discos referenciados por UUID y compartiendo los puntos de montaje. Con el comando `blkid` obtienes la etiqueta , UUID y el sistema de ficheros de un dispositivo de bloques.

Virtualizando ahorramos costes , eso es el lema del movimiento IT actual y creo que tiene razón. A cambio de un mayor trabajo

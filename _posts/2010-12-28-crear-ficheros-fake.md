---
layout: posts
title: "Crear ficheros fake"
date: "2010-12-28"
categories: linux
---

$ cd /tmp
$ dd if=/dev/zero of=prueba.txt bs=1024 count=4194304
4194304+0 registros de entrada
4194304+0 registros de salida
4294967296 bytes (4,3 GB) copiados

El resultado obtenido es un archivo _prueba.txt_ de 4,3GB (1024 \* 4194304 bytes).

Parámetros utilizados

- if – archivo de entrada , en este caso en nada
- of – archivo de salida, el archivo que queremos crear
- bs – tamaño de block en bytes
- count – cantidad de blocks de tamaño bs

Para más detalle , consultar el **man page**

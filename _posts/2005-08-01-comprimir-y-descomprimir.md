---
layout: post
title: "Comprimir y descomprimir"
date: "2005-08-01"
categories: linux
---

Comprimir y descomprimir en linux Supongamos que tenemos un directorio llamado subcarpeta que cuelga de carpeta, si queremos comprimir su contenido en un fichero tar.gz o descomprimir un fichero tar.gz en el directorio carpeta para que se genere toda su estructura de directorios, estos serían los comandos: Comprimir: cd carpeta tar -c subcarpeta >fichero.tar gzip fichero.tar Descomprimir: cd carpeta gunzip fichero.tar.gz tar -xvf fichero.tar Si quieres usar los nuevos ficheros bz2 los comandos son los mismos sustituyendo gzip con bzip2 y gunzip con bunzip2. Los ficheros tar, gz y tar.gz se pueden ver también desde MS-DOS o Windows con algunos compresores como el Windows Commander.

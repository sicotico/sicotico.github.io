---
layout: single
title: "Export e Import en Oracle"
date: "2010-03-16"
categories: software
---

La herramienta basica es exp.exe e import.exe

Para el tributo `file` utilizaremos siempre rutas absolutas.

`file=C:fichero.dmp`

`exp user/pass file=prueba.dmp tables=(tabla1,tabla2) bufer 100000`

Si tienes varias oracle\_home , o instalaciones en una máquina , debes situarte en el directorio BIN para ejecutar el exp.exe  y añadir a que instancia te vas a conectar

`exp user/pass@instancia file=prueba.dmp tables=(tabla1,tabla2) buffer=100000`

Para una importacion completa se debe utilizar el aparametro `full=y`

`exp user/pass@instancia full=yes file=c:prueba.dmp buffer=100000`

Para importar , siguiendo con las mismas indicaciones que para exportar

`imp user/pass@instancia file=prueba.dmp tables=(tabla1,tabla2) buffer=100000`

Fuente: [OraSite.com](https://www.orasite.com/tutoriales/export-import-oracle-9i.html)

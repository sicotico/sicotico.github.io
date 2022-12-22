---
layout: posts
title: "Apache symfony"
date: "2010-11-10"
categories: dev
---

Este es el virtual host creado para albergar un symfony (probando sandbox).

 ServerName miaplicacion.ejemplo.com
DocumentRoot "/dev/sandbox/web"
DirectoryIndex index.php
Alias /sf "/dev/sandbox/lib/vendor/symfony/data/web/sf"
 AllowOverride All
Allow from All 
 AllowOverride All
Allow from All 

Utilizar un alias es para poder tener varios entorno o proyecto corriendo del mismo framework y sea más fácil de administrar , las cosas bien hechas desde el principio.

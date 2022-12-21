---
layout: post
title: "Java SE Floating Point Updater"
date: "2012-07-17"
categories: dev
---

Este jar es un parche peculiar para las JRE , evita varios ataque de denegación de servicio y varias operaciones.

La instalación:

Descargar el parche de oracle Copiarlo en la caperta bin del jre y  ejecutar:

java -jar "nombre del paquete" -u -v

El log para revisar posibles fallos es:

`.fpupdater.log`

El backaup del fp.jar que actualiza se llama

`fp.jar.fpupdater`

Si has de reinstalarlo con eliminar el log y el backup se puede relanzar

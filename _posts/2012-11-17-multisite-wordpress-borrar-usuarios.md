---
layout: post
title: "Multisite Wordpress - Borrar usuarios y sites"
date: "2012-11-17"
categories: dev
---

## WP Multisite

Llevo una temporada trabajando con WordPress Multisite , tiene sus cosas buenas y sus cosas malas . Actualmente estoy probado funcionalidades según usuarios  y se hace complicado dar de alta sitios y usuarios. Siempre aparece el típico mensaje de ese usuario estará libre es un par de días. Gracioso pero incordia un poco.

Habilitar WP Multisite en WordPress afecta al esquema de tablas , así que el punto clave a revisar es la base de datos.

Algo había que hacer , así que manos a la obra. Las prisas son malas consejeras así que directamente a la base  de datos borrar registro , eso nada de por intuición. el olfateo ya lo he hecho y he apuntado lo que tenemos que borrar.

Estas son las tablas que mantiene el control de los registros

- wp\_registrations
- wp\_singup

En estas dos tablas tendremos los usuarios registras vía wp-singup.php , eliminamos los registros y  no aparecerán esos mensajes tan odiosos

\[caption id="" align="aligncenter" width="640"\]![error_singup_wp](images/8169563304_b1d35c6d5b_z.jpg "Multisite") Formulario de alta en WP Multisite\[/caption\]

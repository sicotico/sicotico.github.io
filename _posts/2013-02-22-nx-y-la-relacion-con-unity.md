---
layout: single
title: "NX y la relación con Unity"
date: "2013-02-22"
categories: dev
---

# NX Simple amor y odio , o más bien dejadez.

Pues eso dejadez , no ha parcheado las versiones de NX para soportar el Gestor de ventana de Unity. No se como he llegado a este post

[https://pleirb.blogspot.com.es/2012/08/como-hacer-que-funcione-bien-free-nx-en.html](https://pleirb.blogspot.com.es/2012/08/como-hacer-que-funcione-bien-free-nx-en.html "como-hacer-que-funcione-bien-free-nx-en")

pero especifican el nuevo comando de gestión para GNOME , perdemos la conectividad con GNOME pero bueno ganamos la que nos interesa Unity

\[caption id="" align="alignleft" width="300"\]![Logo NoMachine](images/nomachinezz3.png) Logo NoMachine\[/caption\]

\[caption id="" align="alignright" width="250"\]![Logo Unity](images/unity_logo.jpg) Logo Unity\[/caption\]

 

### Instrucciones

En el ficheros/usr/NX/etc/node.cfg Localizar la variable  "CommandStartGnome" Asignamos este valor: **`"env DESKTOP_SESSION=ubuntu-2d GDMSESSION=ubuntu-2d /etc/X11/Xsession '/usr/bin/gnome-session --session=ubuntu-2d'"`**

Valor antiguo: `"/etc/X11/Xsession gnome-session"`

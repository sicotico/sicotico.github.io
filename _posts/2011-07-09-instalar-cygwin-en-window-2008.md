---
layout: post
title: "Instalar cygwin en Window 2008"
date: "2011-07-09"
categories: windows linux
---

Los paso básicos par al instalación , siguiendo como estándar a menos paquetes mejor , menos problemas.

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736706492\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736156405\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736156465\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736706644\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736156607\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736706804\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736156823\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736706950\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736707052\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736157037\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736707130\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736157125\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736157163\[/flickr\]

Ya tenemos instalado cygwin. Ahora vamos a trabajar con los usuarios. En este caso hay que generar los típicos ficheros groups y passwd. Para ello tenemos un par de herramientas que nos generan los ficheros con los mismos datos que nuestro equipo Windows.

Crea el archivo de usuarios

$ mkpasswd -l > /etc/passwd

Y ahora el archivo de grupos

$ mkgroup -l > /etc/group

Por ultimo asignamos permisos de lectura a los dos ficheros

$ chmod +r /etc/passwd

$ chmod +r /etc/group

Ya lo tenemos instalado de forma básica y con usuario !!!

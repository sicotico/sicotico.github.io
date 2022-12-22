---
layout: posts
title: "Error error_APT::Default-Release"
date: "2012-07-12"
categories: linux
---

Este fallo es conocido dentro de las configuraciones de apt. Es así un error del cliente de los repositorios. Como existe varios clientes

- apt-get
- aptitude
- synaptic

Cada uno tiene su configuración y la forma de resolverla es igual. Se almacena de forma errónea un nombre de distribución que no concuerda con los repositorios activados.

En apt-get el fichero `/etc/apt/apt.conf se localiza la linea`

APT::Default-Release "stable";

`_"stable"_ es el repositorio que ya no tenemos activo en nuestras fuentes`

Error en Synaptics: [![error_APT::Default-Release](images/7376420576_f8156a3c6b.jpg)](https://www.flickr.com/photos/12949201@N08/7376420576/ "error_APT::Default-Release por sicotico, en Flickr")

Para synaptics cambia el nombre de la linea por:

DefaultDistro "stable";

Y el fichero `/root/.synaptic/synaptic.conf`

 

Fuentes:

[bugs.launchpad.net](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/842179)

[manpages apt\_preferences](https://manpages.ubuntu.com/manpages/maverick/es/man5/apt_preferences.5.html "apt_preferences")

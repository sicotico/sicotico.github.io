---
layout: posts
title: "Antes Synaptic , ahora terminal"
date: "2012-02-21"
categories: linux
---

Con el pequeño server en casa y lo agarrado que fui al instalar el SO en un pincho de 4GB , ahora vienen trabajo extra. Hay que limpiar !!! y ya no tengo synaptics. Básicamente he pensado en las opciones que me proporcionaba y he buscado sus homologas en consola.

Me he ayudado de _deborphan_ , hace tiempo lo utilice y ha sido mi primer reflejo al pensar en esta tarea.

sudo apt-get install deborphan
sudo apt-get --purge remove \`deborphan\`
sudo apt-get --purge remove \`deborphan --libdev\`
sudo dpkg --purge $(deborphan --find-config)
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

TOMA YA !!! Si después de esto os quedan poco espacio , creo que lo hay que buscar son ficheros nuestros en vez de paquetes.

 

Fuente [esdebian](https://www.esdebian.org/wiki/mantener-limpio-sistema-instalado-debian "Limpiar el sistema")

---
layout: post
title: "Bug Gnome-mount"
date: "2007-07-02"
categories: linux
---

Con la nueva versión 7.04 se añadio funciones adicionales sobre auto montaje de unidades extraibles No se ha documentado bien y se ha generado un bug el [#107668 "Setting an invalid mount point can make a removeable media unaccessible"](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/107668).

La nueva funcionalidad es decir a Gnome\-manager\-volumen que una unidad extraible se monte siempre en la misma carpeta , por tanto  con el mismo nombre en el escritorio. El problema esta en que el cuadro de dialogo que se nos muestra

![](images/gnome1.png)

Hay que rellenarlo como indica la imagen , se da simplemente su carpeta ya que el toma como base " /media/ "

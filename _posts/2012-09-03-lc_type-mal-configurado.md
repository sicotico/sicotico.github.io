---
layout: posts
title: "LC_TYPE mal configurado"
date: "2012-09-03"
categories: linux
---

Este error se identifica , en mi caso , al utilizar el auto completado en consola. Cada vez que lo invoco aparece este mensaje

sh: warning: setlocale: LC\_CTYPE: cannot change locale (es\_ES.UTF-8)/

Para asignarlo correctamente debemos revisar que tengamos esto paquetes instalados

sudo apt-get install language-pack-gnome-es language-pack-gnome-es-base

Ahora generaremos de nuevo los "locales" del equipo mediante

sudo locale-gen es\_ES es\_ES.UTF-8 es\_ES es\_ES.UTF-8

Y luego los asignaremos a la configuración por defecto del paquete:

sudo dpkg-reconfigure locales

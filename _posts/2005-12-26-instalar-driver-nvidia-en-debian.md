---
layout: post
title: "Instalar Driver nVidia en Debian"
date: "2005-12-26"
categories: linux
---

Pues vamos a usar el paquete module-assistant , asi que hay que instalarlo:

_#apt-get install modules-assistant_

busquemos los headers y sources de nuestro kernel

_#uname -a_

_#apt-get install kernel-header__\-<mi version>_ _kernel-source__\-<mi version>_ _nvidia__\-kernel-source_

Ahora instalaremos el modulo

_#modules-assistant auto-install nvidia-kernel-source_

o

_#m-a a-i nvidia-kernel-source_

Después de haber echo esto , hay que configurar el servidor de las X , asi que hacerlo al estilo debian (ubuntu):

_#dpkg-reconfigure xserver-xorg_

y seleccionar driver nvidia

o

_#cp /etc/X11/xorg.conf /etc/X11/xorg.conf-1_

_#pico /etc/X11/xorg.conf_

y modificar la linea Driver "vesa o nv" y poner Driver "nvidia"

esto es opcional , en la seccion Device añadir

Option "RenderAccel" "true"

Option "NvAGP" "1"

Option "NoLogo" #para evitar que aparezca el logo de nvidia se pone

El resultado final seri aalgo parecido a esto

Mi seccion _Device_ del fichero _/etc/X11/xorg.conf_

_Section "Device" identifier "nVidia FX5700go" busid "PCI:3:0:0"_

_driver "nvidia" screen 0_

_Option "RenderAccel" "true"_

_Option "NvAGP" "1"_

_Option "NoLogo" #para evitar que aparezca el logo de nvidia se pone_

_EndSection_

_#md5sum /etc/X11/xorg.conf > /var/lib/xfree86/ xorg.conf.md5sum_

Esto seria la forma tipo "non-packages" resto de slack , en mi debian64 sarge ,porque etch y sid estan muy mal los paquetes estamos en modo estable. Pues la forma mas facil es instalar nuestro x-window-system-core , fluxbox y gcc-3.4 porque hace falta ya que fue con lo que se compilo los kernels de sarge. El detalle esta en modificar el enlace simbolico de /usr/bin/gcc --> gcc-3.3 , hacia un gcc-3.4 . Ahora y nos podemos bajar el driver de la web de nVIDIA he instalrlo por le metodo rustico pero mas que fiable #sh

---
layout: single
title: "de KDE a GNOME"
date: "2012-05-17"
categories: linux
---

Una temporada probado KDE y recordando los viejos tiempos , en mi slackware solo usaba KDE y compilado por mi. Si hacia estas cosas mientras estaba en la universidad , 26 horas de compilación en un Acer 290TM Centrino a 1,5Ghz. Un trabajo sencillo gracias a scripts preparados por la mejor distro de linux que he utilizado. El trabajo divertido entraba en el gcc y la parametrización para el procesador , jo que tiempos!!!.

He probado KDE 4 otra vez , pero con Kubuntu y  tras días de uso he decidido abandonar este escritorio y quedarme con el buen sabor de boca que me dejo en mis inicios. Me vuelvo a GNOME

El tiempo ahora es escaso asi que gracias a la paquetería de tipo debian he podido pasar de un escritorio a otro sin formatear. Mis configuraciones han permanecido intactas y eso no dejan de ser horas de trabajo

 **Los paso seguidos** , en medida de lo posible porque lo he de sacado de mi historial de terminal y y ano me acuerdo porque hice algunas cosas.

Pasamos a un terminal de sistema

Control+F1

Paramos el servicio KDM

sudo service kdm stop

Buscamos los paquetes de KDE , para tener una visión global

sudo aptitude search kde | grep ^i

Yo creo que esta linea no me funcionó

sudo aptitude purge | aptitude search kde | grep ^i

Tire de aptitude para eliminar todo KDE , desde "tareas" existe la sección de KDE y simplemente eliminé todo , con la opción purge.

Prepárate porque me senté el e sofá y vi Italian Job de tirón

Después rematé los últimos paquetes con una busqueda

sudo aptitude purge kdelibs5-data
sudo aptitude purge libkde\*
sudo apt-get purge libkde\*
sudo aptitude purge | aptitude search kde | grep ^i
sudo aptitude search kde | grep ^i
sudo apt-get purge language-pack-kde-\*
sudo aptitude search kde | grep ^i

Otra vez con aptitude y desde "tareas"  simplemente instalé GNOME.

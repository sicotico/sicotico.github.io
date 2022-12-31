---
layout: single
title: "Amarok ese gran desconocido…………."
date: "2006-06-09"
categories: linux
---

Desconocido en su funcionamiento ya que es el reproductor  predeterminado de KDE. Siendo así no es es mas que un front-end muy bonito en qt el que necesita un motor multimedia y unos codecs. En una distro como Kubuntu vienen todos instalados pero para una debian o gentoo es interesante saber que paquetes son los "buenos". No hay ninguna razón para comentar que es si es malo sino que el motor multimedia que usa no es bueno o como dicen por google hay que ver cual va mejor a nuestro equipo.

Todo el mundo conoce el gstreamer , mil paquetes cada uno con las instrucciones para leer un determinado formato o comprimir a el , bueno pues es el opuesto de xine un motor multimedia mas que un reproductor.

Tras las presentaciones solo debemos elegir que motor deseamos en ambos casos necesitaremos el paquete de amarok , y amarok-gstreamer o amarok-xine y amarok-engines , estos son los paquetes que dirigiran el "cotarro" en amarok así que en función de esta elección usaremos xine o gstreamer. Después de la instalación de cualquiera de los dos motores necesitamos ir al amarok Preferencias --> Configurar Amarok --> motor   y seleccionar "xine" o "gstreamer".

 Para Xine necesitamos instalar  los paquetes libxine-extracodecs  , y esto valdrá para reproducir mp3 pero como yo uso kde y viene provisto de arts recomiendo el paquete amarok-arts para intentar dirigir el programa hacia arts y así no secuestrar "/dev/dsp".

Para gstreamer necesitamos instalar algun paquete mas ya que este se distribuye muy modulado , gstreamer0.10-arts o  gstreamer0.10-esd y  gstreamer0.10-alsa , gstreamer0.10-gl ,  gstreamer0.10-ffmpg , con eso seria lo mínimo , siempre puedes revisar la lista de plugins que tiene este motor multimedia que son decenas para elegir.

---
layout: single
title: "Audio+Video en HDMI Nvidia 9500gs"
date: "2009-10-15"
categories: hardware
---

El otro día encontré un cable de 10 metros de hdmi a 20€ y claro no pude más que pillarlo. Ahora tengo en casa mi sobremesa conectado a la tele del salón , con un solo cable.

La cosa esta en que la salida de hdmi esta en la tarjeta gráfica , y esta no tiene sonido. Es desde hace tiempo es un pensamiento erróneo , tienen un chip de sonido que en mi caso unen físicamente la tarjeta de sonido y la gráfica. Parece que con eso ya debería estar todo , me dispongo a probarlo y que el sonido no sale. Buscamos por internet y encontramos en [ubuntuforums](https://ubuntuforums.org/showthread.php?p=6589810) una primera ayuda. Necesitamos una version más nueva , mi kubuntu 9.04 trae ALSA 1.0.18 y necesitamos una 1.0.20. Esto lo comprobamos con:

`cat /proc/asound/version`

Desde ubuntuforums puedes encontrar un maravilloso [script](https://ubuntuforums.org/attachment.php?s=c736786fc8d891f3b9f0284c138468fb&attachmentid=128874&d=1253177665) que te sube la versión , algo maravilloso ya que no se toca repositorios.

1. cd Directorio-donde-lo-has-descargado
2. tar xvf AlsaUpgrade-1.0.21-4.tar
3. sudo ./AlsaUpgrade-1.0.21-4.sh -di
Tranquilo a partir de ahora el ritmo lo marca el script asi que tomártelo con paciencia , yo estuve 20 minutos esperando  y volverás a tener el control.4. Reinicia el PC y listo.

Ahora es cuando lees que has terminado y si te pasa como a mi , pues no te va . Hay que hacer apaños en modo duro , vamos a por el modulo del kernel.

Tenemos un chiset nvidia y una tarjeta de sonido en teoría también nvidia MCP61 , digo en teoría porque el chiset que usa es uno genérico , pero que muy genérico , de nombre ALC . Este chip se implantó en miles de modelos y los pioneros fueron los de intel , asi que el modulo del kernel para el sonido es el `snd-intel`

En el fichero `/etc/modprobe.d/alsasound` añadimos esta linea:

`options snd-hda-intel index=0 model=3stack-dig`

No voy tocar ninguna configuración de alsa ya que en mi caso también uso sonido la mesa pc . Lo que utilizo es el VLC y en Audio-->Dispositivo de salida-->Audio 5.1

Como curiosidad  en nvidia TwinView para maximizar el video en la pantalla secundaria hay que mover los mandos de vlc a esa pantalla.

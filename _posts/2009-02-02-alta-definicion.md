---
layout: single
title: "alta definicion en ATI"
date: "2009-02-02"
categories: hardware
---

Tengo este portátil:

Dell 1501 primera infraestructura de bajo consumo ATI/AMD

Turionx2 64 a 1,6Mhz por nucleo

ChipSet ATI RS480 (Audio , SATA ,USB .. )

Gráfica integrada en plaza ATI Xpress 200m 128MB dedicados (PowerSave)

No me reproducía películas en alta definición.

Probé el mplayer si que que lo hacía , no tenia sentido así que  investigamos un poco y al probar xine te avisaba que no había compatibilidad con Xv (X-Video). Mplayer lleva su configuración y venía con acceso directo a Xv Documentación de ATI y BINGO !!!!

Comprobar el correcto soporte de Xv existe la herramienta xvinfo

`X-Video Extension version 2.2 screen #0 Adaptor #0: "ATI Radeon Video Overlay"` En caso de error utilizar la herramienta oficial de ati `aticonfig --overlay-on=0 aticonfig --overlay-type=xv` reiniciamos ya que a tiempo real no podemos reconfigurar el servidor de x

xorg.conf

Section "Device" \[..\] Driver "fglrx" Option "OverlayOnCRTC" "0" Option "VideoOverlay" "on" Option "OpenGLOverlay" "off" \[..\] EndSection

Actualización:

`mirror              2 screens - same content, identical refresh rate/resolution Note: This option is NOT supported with Avivo`

Para aprovechar el rendimiento la mejor opción es configurar como escritorio expandido.GXine es el reproductor con mayor calidad.

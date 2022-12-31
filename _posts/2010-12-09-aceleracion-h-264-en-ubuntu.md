---
layout: single
title: "Aceleración H.264 en Ubuntu"
date: "2010-12-09"
categories: linux
---

Reproducción mediante la API VDPAU( Mas info en [Wikiepedia/VDPAU](https://es.wikipedia.org/wiki/VDPAU))

NVIDIA serie 8000 y superiores, excepto 8800, el apoyo Video Decode y Presentación API para Unix (VDPAU). Esto permite a la GPU de Nvidia para asumir parte de la carga de decodificación.

Mplayer en Ubuntu 10.10 soporta VDPAU. Yo he tenido que instalar el paquete el paquete `libvdpau`.

Cuando usted tiene un sistema de archivos descifrados Blu-ray/HD-DVD en el disco duro, puede ejecutar el siguiente comando: H.264 disc

mplayer -vc ffh264vdpau -vo vdpau ~/BDMV/STREAM/00001.m2ts

VC-1 disc

mplayer -vc ffvc1vdpau -vo vdpau ~/BDMV/STREAM/00001.m2ts

MPEG disc

mplayer -vc ffmpeg12vdpau -vo vdpau ~/BDMV/STREAM/00001.m2ts

Fuente: [Community Ubuntu Documentation](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---
layout: posts
title: "Conversión entre formatos de audio"
date: "2007-08-18"
categories: software linux
---

**Monkey's Audio --> wav**

Usaremos el programa mac , el cual ha perdido su pagina de sourceforge , así que he subido el paquete [deb a mi pagina](https://sicotico.googlepages.com/mac-3.99-u4_b3-1_i386.deb).

Si usamos consola:

_\# sudo dpkg -i mac-3.99-u4\_b3-1\_i386.deb_

Si usamos Modo grafico:

Ubuntu integra gtk-gdebi y con darle dos clicks se abrirá un dialogo de instalación.

MAC se usa en consola:

_#mac archivo.ape archivo.wav -d_

**WAV --> Varios Formatos (Ogg Vorbis ,MP3,FLAC)**

Yo he usado el programa SoundConvert disponible en repositorios de Debian y Ubuntu

**WAV --> FLAC**

Instalamos el paquete flac

_#sudo aptitude install flac_ 

_#flac -8 archivo.wav_

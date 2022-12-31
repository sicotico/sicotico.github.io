---
layout: single
title: "Repositorios Ubuntu."
date: "2006-08-17"
categories: linux
---

La explicacion para que podais seleccionarlos de forma optima , seria no usar los españoles , y que se estructuran en servidores nacional , internacional , de seguridad y novedosdo comercial. Dentro de ellso exiten las divisioens normales de universe , multiverse restricted y main , pero bueno eso son pijadas de programas mantenidos por ubuntu o por la comunidad.

el detalle nuevo de los "comercial" bueno de "el" porque solo conozco uno a nivel mundial , es meter software no opensource y diremos sacrilegio pero el plugin de Flash no es opensource y esta en repositrorios normales y nadie dice nada , asi que ahora esta disponible Opera 9+ y RealPlayer en este repositorio , espero que reordenen paquete sy flash tambien termine aqui , para ser todo coherentes.

Mi sources.list:

#-------------------------------------------------------------------------------------- #-------------------------------------------------------------------------------------- #Repositorio Español

deb https://es.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse deb-src https://es.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb https://es.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse deb-src https://es.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb https://es.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse deb-src https://es.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

#-------------------------------------------------------------------------------------- #-------------------------------------------------------------------------------------- #Repositorio Internacional

deb https://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse deb-src https://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse

deb https://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse deb-src https://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

deb https://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse deb-src https://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

#-------------------------------------------------------------------------------------- #-------------------------------------------------------------------------------------- #Repositorio Security (el mas actualizado y de seguridad)

deb https://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse deb-src https://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb https://security.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse deb-src https://security.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

deb https://security.ubuntu.com/ubuntu dapper main restricted universe multiverse deb-src https://security.ubuntu.com/ubuntu dapper main restricted universe multiverse

#-------------------------------------------------------------------------------------- #-------------------------------------------------------------------------------------- #Repositorio De Automix , lo tengo comentado tras haberlo usado uan vez. # deb https://www.getautomatix.com/apt dapper main

#-------------------------------------------------------------------------------------- #-------------------------------------------------------------------------------------- #Repositorio de VLC

deb https://download.videolan.org/pub/videolan/debian sarge main deb-src https://download.videolan.org/pub/videolan/debian sarge main

#-------------------------------------------------------------------------------------- #-------------------------------------------------------------------------------------- #Repositorio de aMule

deb https://amule-debian.dyndns.org/ debian/

#-------------------------------------------------------------------------------------- #-------------------------------------------------------------------------------------- #Repositorio Dapper comercial

deb https://archive.canonical.com/ubuntu dapper-commercial main

#--------------------------------------------------------------------------------------

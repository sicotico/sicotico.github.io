---
layout: post
title: "Sarge AMD64 (Powernow)"
date: "2005-09-25"
categories: 
  - "sin-categoria"
---

icotico ...

Despues de investigar sobre los rumores de versiones de debian para amd64 , nos encontramos con que existen versiones sarge y sid , pero que estas son "unofficial" bueno o en mayo rparte ya que como dice el archivo de README.html del cd net-install-sarge-amd64 :

About This CD This CD-ROM is labeled Debian GNU/Linux 3.1 r0a "Sarge" - Official amd64 Binary-1

Así que nos encontramos con una versión oficial y no oficial .

Despues de estos lios burocráticos vamso a ver la forma de optimizar un amd64 con una debian personal , es como queda el acabado mas bonito .

Mi sources.list (/etc/apt/sources.list) solo tiene un repositorio y aque casi todos los mirror me han dado algun fallo.

deb ftp://ftp.es.debian.org/debian sid main contrib non-free deb ftp://ftp.es.debian.org/debian sarge main contrib non-free

Yo no puedo vivir sin "SiD"...... (xorg)

Bueno lo primero es poner el maravillosos control de energía que poseen estos magníficos equipos , como se puede notar yo tengo uno , lo primero cargar el modulo de nuestro procesador

#cd /lib/modules/2.6.12/kernel/arch/x84\_64/kernel/cpufreq #ls acpi-cpufreq.ko powernow-k8.ko speedstep-centrino.ko #su(pasar a modo superuser) #modprobe powernow-k8 #modprobe cpufreq\_powersave #modprobe cpufreq\_userspace

(esto añadirá la carga del modulo en el arraque) #echo "powernow-k8" >> /etc/modules #echo "cpufreq\_userspace" >> /etc/modules

#apt-get install powernowd

powernowd va a ser el interface para modificar la velocidad de nuestro micro cuando queramos , siempre dentro de unos limites.

#powernowd -s 2200000 (en KHZ)

equivale a 2,2GHZ o 2200MHZ consulatar el man

#man powernowd

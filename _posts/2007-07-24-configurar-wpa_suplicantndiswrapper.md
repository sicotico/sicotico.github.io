---
layout: single
title: "Configurar wpa_suplicant+NdisWrapper"
date: "2007-07-24"
categories: linux hardware
---

Software que tengo instalado.

Ubuntu 7.04

Kernel-386

Driver Ndiswrapper + [bcmwl5](https://sicotico.googlepages.com/bcm43xx.tar.gz)

Wpa\_supplicant

Configurar wpa\_supplicat necesita crear el fichero /etc/wpa\_supplicant.conf a partir de un "/usr/share/doc/wpasupplicant/examples/wpa\_supplicant.con-exambples"

EL fichero de configuración necesita la clave codificada y un bloque network. Esto se consigue con el comando :

#sudo wpa\_passphrase ssid passphrase

La salida es algo parecido a esto:

network={ ssid="missid" #psk="passprase" psk=de03d52a598b1487e25ea0ab720ec372dda73f11f046225849651a4037daf55e } sudo ifconfig eth1 up && sudo wpa\_supplicant -Dwext -ieth1 -c/etc/wpa\_supplicant.conf -dd

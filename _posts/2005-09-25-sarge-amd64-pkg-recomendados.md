---
layout: posts
title: "Sarge AMD64 (pkg recomendados)"
date: "2005-09-25"
categories: linux
---
Ahora recomendaremos lo mínimo a instalar en un Sarge/Sid:

El sources.list al menos tendrá : deb ftp://ftp.es.debian.org/debian sid main contrib non-free deb ftp://ftp.es.debian.org/debian sarge main contrib non-free

#apt-get update #apt-get dist-upgrade

PAQUETES DESCRIPCIÓN

x-window-system --> Servidor de X xorg si tienes sid en el sources.list kde --> Ventanas (si eres muy friki lo puedes cambiar por fluxbox) cupssys hpijs foomatic-db-hpijs --> impresoras y drivers swat smbfs samba samba-common smb4k smbclient --> Comparticion LinuxWin webmin --> para configuracionss del sistema , mas faciles de hacer linux-image-2.6.12-amd64-k8 linux-headers-amd64-k8 linux-source-2.6.12 -->Kernel alsa-base alsa-headers alsa-utils --> ALSA drivers Trj. de Sonido mozilla-firefox mozilla-firefox-locale-es\_es --> Navegador Web

Para personas normales:

#apt-get install x-window-system kde cupssys hpijs foomatic-db-hpijs swat smbfs samba samba-common webmin smb4k smbclient linux-image-2.6.12-amd64-k8 linux-headers-amd64-k8 linux-source-2.6.12 links2 alsa-base alsa-headers alsa-utils mozilla-firefox mozilla-firefox-locale-es\_es

Para personas no normales "frikis":

#apt-get install x-window-system fluxbox cupssys hpijs foomatic-db-hpijs swat smbfs samba samba-common webmin smb4k smbclient linux-image-2.6.12-1-amd64-k8 linux-headers-2.6.12-1-amd64-k8 linux-source-2.6.12 links2 alsa-base alsa-headers alsa-utils madplay vlc xterm mozilla-firefox mozilla-firefox-locale-es\_es

Con esto ya esta todo tendrás un sistema actualizado con lo mínimo para empezar, ahora solo que personalizarlo.....

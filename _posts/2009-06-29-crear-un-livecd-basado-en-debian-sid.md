---
layout: single
title: "Crear un LiveCD basado en Debian Sid"
date: "2009-06-29"
categories: linux
---

Instalamos live-helper y si somos muy vagos y no queremos personalizar nada live-magic

`apt-get install live-helper live-magic`

Creo un fichero con los paquetes a instalar  "lista de paquetes"

`/usr/share/live-helper/list/<nombre de la lista>`

\# /usr/share/live-helper/lists/standard - package list for live-helper(7)

\## LH: Standard #include <minimal>

console-common kbd locales madwifi-tools python vim build-essential linux-image-686 netbase bin-utils util-linux mc module-assistant Creamos una carpeta  nos situamos dentro

sudo lh\_config -p inta --root-command sudo --bootloader syslinux -b iso -a i386 --username <nombre de usuario> --distribution sid --apt aptitude --mirror-chroot "ftp://ftp.fr.debian.org/debian/" --mirror-bootstrap "ftp://ftp.fr.debian.org/debian/" --mirror-binary "ftp://ftp.fr.debian.org/debian/" --bootappend-live "locale=es\_ES.UTF-8 keyb=es"

Esto es hacerlo como los hombre , lo cual a veces es tedioso y trabajoso. El otro programita que nos instalamos el live-magic , no nos deja muchas opciones pero en apenas un minuto y otros de descarga de paquetes y proceso tendremos una live bien bonita

Fuentes:

[CRySOL - Debian Live personalizada en una línea](https://crysol.org/es/node/1114)

[Organizing Linux Information! - HOWTO: 5 minutes to creating bootable Debian LiveCDs, USB Live, and netboot/NFS images](https://blogs.koolwal.net/2009/04/27/howto-5-minutes-to-creating-bootable-debian-livecds-and-netboot-images/)

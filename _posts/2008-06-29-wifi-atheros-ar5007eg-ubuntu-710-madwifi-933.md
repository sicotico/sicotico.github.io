---
layout: single
title: "Wifi Atheros AR5007EG Ubuntu 7.10 y 8.04 MadWifi 9.3.3"
date: "2008-06-29"
categories: hardware linux
---

## Identificar Hardware

Para verficar que tenemos esta tarjeta debemos de hacer un `" lspci -nn | grep 168c:001c" y saldra :`

`Ethernet Controller []:Atheros Communications, Inc. "AR5006EG" 802.11 b/g Wireless PCI Express Adapter [168c:001c]`

No coincide el nombre del modelo , pero no pasa nada ya que eso debe de ocurrir , ahora verificamos un dmesg en busca de un error de HAL . `HAL status 13`

Con esto hemos confirmado que es un 5007 en vez de la 5006 que nos mostraba antes.

## Requisitos

Para hacer funcionar esta tarjeta necesitamos una versión específica del SVN de Madwifi y un parche. Para más facilidad utilizaremos una snapshot , que no es mas que la carpeta del SVN comprimidad y numerada con la fecha del dia y el parche aplicado.

Este parche solo es balido para plataformas de **32-bits** x86 incluyendo i686 y AMD CPUs

Necesitamos el Madwifi driver snapshot r2756.

## Procedimiento para aplicar este parche[](https://madwifi.org/ticket/1679#Toapplythepatch "Permalink to Toapplythepatch")

1\. Descargamos el Madwifi driver snapshot [r2756](https://madwifi.org/changeset/2756 "Linux 2.6.24 moves proc_net inside init_net") usando el siguiente enlace.

[snapshots.madwifi.org/madwifi-ng/madwifi-ng-](https://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz)[r2756](https://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz)[\-20071018.tar.gz](https://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz)

2\. Extraemos este driver y nos situamos dentro del directorio.

`prompt> tar -xvzf madwifi-ng-r2756-20071018.tar.gz prompt> cd madwifi-ng-r2756-20071018/`

3\. Descargamos el patch usando el siguiente enlace y usanso la opción guardar fichero.

[madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw](https://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw)

4\. Aplicamos el parche. `prompt> patch -p0 < madwifi-ng-0933.ar2425.20071130.i386.patch`

Podemos usar esta descarga que ya contiene el código parcheado

[https://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](https://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

5\. Si usas Ubuntu debdes de bloquear la versionde madwifi interna

Editamos el fichero /etc/default/linux-restricted-modules-common

`#sudo vi /etc/default/linux-restricted-modules-common`

`DISABLED_MODULES=ath_hal`

Podemos reiniciar para que el cambio tenga efecto o ejecutar

`#modprobe -r ath_pci && modprobe -r ath_hal`

6\. Ahora compilamos e intalamos este driver parcheado `prompt> sudo make && sudo make install` `prompt> modprobe ath_pci`

Actualización:

Funciona el modo monitor con esta tarjeta

`#wlanconfig ath0 destroy`

`#wlanconfig ath create wlandev wifi wlanmode monitor`

**Probada  en ubuntu 8.04  perfectamente**

Sigue con la misma limitación de Kernel 386 , pero por lo menos funciona sin Ndis y se puede poner en modo monitor

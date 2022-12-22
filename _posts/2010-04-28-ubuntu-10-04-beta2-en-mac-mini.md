---
layout: posts
title: "Ubuntu 10.04 beta2 en Mac mini"
date: "2010-04-28"
categories: linux
---

La verdad , me ha costado un poco eso del arranque EFI pero bueno Wikipedia ahí está:

**La Interfaz Extensible del Firmware, Extensible Firmware Interface (EFI),** es una especificación desarrollada por Intel dirigida a reemplazar la antigua interfaz del estándar IBM PC BIOS (la cual se ha estado implementando por los fabricantes de computadores personales desde que salió a luz el primer IBM PC hasta hoy), se ha implementado en los computadores Macintosh de Apple con procesador Intel. El objetivo de esta Interfaz es establecer la forma en que un software específico como un Sistema Operativo o una aplicación de arranque debe acceder a los recursos del sistema.

Evitando eso , simplemente hay que re-dimensionar la partición de Mac OS X y eso se puede hacer con el sistema operativo en caliente. Ahí es donde sorprende un núcleo Match (BSD - UNIX).

### Instalando gestor de SO.

Lo primero es instalar rEFIt , un aplicación de tipo dmg para Mac , este nos prorciona un gestor de arranque preparado para EFI. Yo no me fiaba mucho de la instalación , soy un escéptico ,  reinicie y bingo aparece un selector

[![](images/screen2.png "rEFIt")](https://refit.sourceforge.net/img/screen2.png)

### Preparando las particiones

`sudo diskutil list`

/dev/disk0 #:                TYPE                                         NAME                                      SIZE             IDENTIFIER 0:                GUID\_partition\_scheme                                                    \*160.0 GB    disk0 1:                 EFI                                                                                                209.7 MB    disk0s1 2:                Apple\_HFS                             Macintosh HD                      159.0 GB        disk0s2

Obtenemos la tabla de particiones de todos los disco conectados , incluso DVD o CD , es lo que tiene que todo sean ficheros

`sudo diskutil resizeVolume disk0s2 60G "MS-DOS FAT32"`

Simplemente re dimensiono la partición de sistema operativo , hay gente que ademas crean desde aquí las particiones , mejor un comando una acción.

### Instalando Ubuntu

Aquí utilice el espacio libre que genere al re-dimensionar la partición de 159GB a 60GB para Mac OS X. Seguí la técnica habitual de partición de Swap 2GB igual que mi RAM , 15 GB para la partición de sistema **_/_** en ext4 y 80,7GB también en ext4 para _**/home**_

Yo utilice el DVD de Ubuntu beta 2 , por impaciente ,  y no me pidió muchas más que la cuenta de sistema.

### Esto final de las particiones

Al final la tabla de particiones debería quedar así

`sudo diskutil list`

/dev/disk0 #:                 TYPE                                         NAME                                      SIZE             IDENTIFIER 0:                 GUID\_partition\_scheme                                                    \*160.0 GB    disk0 1:                  EFI                                                                                                209.7 MB    disk0s1 2:                 Apple\_HFS                             Macintosh HD                      60.0 GB        disk0s2 3:                 Linux Swap                                                                                4.1 GB            disk0s3 4:                 Microsoft Basic Data          UNTITLED                             15.0 GB         disk0s4 5:                 Microsoft Basic Data          UNTITLED                             80.7 GB        disk0s5

### **Fuentes:**

[**Interfaz Extensible del Firmware**, _**Extensible Firmware Interface**_ (**EFI**)](https://es.wikipedia.org/wiki/Extensible_Firmware_Interface)

[**Match (Núcleo)**](https://es.wikipedia.org/wiki/Mach_%28n%C3%BAcleo%29)

[**Mac OS X**](https://es.wikipedia.org/wiki/Mac_OS_X)

**[rEFIt](https://refit.sourceforge.net/)**

[**Manual del OtroLado.net**](https://www.elotrolado.net/hilo_gu-a-triple-boot-en-mactels-leopard-ub-9-04-win7-rc_1257251#p1716513619)

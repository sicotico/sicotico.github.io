---
layout: single
title: "Como redimensionar la swap en Debian 6"
date: "2011-08-26"
categories: linux
---

Verificamos si esta activada la swap:  
  
**free**  
  
             total       used       free     shared    buffers     cached  
Mem:       1027264      64220     963044          0       6012      19464  
\-/+ buffers/cache:      38744     988520  
**Swap:       522232          0     522232**  
  
Antes que nada hay que desactivarla:  
  
**sudo swapoff -a**  
  
**free**  
  
             total       used       free     shared    buffers     cached  
Mem:       1027264      63388     963876          0       5984      18732  
\-/+ buffers/cache:      38672     988592  
**Swap:            0          0          0**  
  
Comprobamos en que device esta montada la swap mirando el fichero "fstab" de /etc:  
  
**cat /etc/fstab**  
  
\# swap was on **/dev/sdj1** during installation  
UUID=**f8ff33ba-79ad-4fc0-887e-6f701e78fd3d** none            **swap**    sw              0       0  
  
Comprobamos a que device corresponde el UUID:  
  
**ls -l /dev/disk/by-uuid/**  
  
lrwxrwxrwx 1 root root 10 ago 26 10:18 **f8ff33ba-79ad-4fc0-887e-6f701e78fd3d** -> ../../**sdj1**  
  
Comprobamos de cuanto espacio libre disponemos:  
  
**sudo parted /dev/sdj print free**  
  
Model: ATA VBOX HARDDISK (scsi)  
Disk /dev/sdj: 1342MB  
Sector size (logical/physical): 512B/512B  
Partition Table: msdos  
  
Number  Start   End     Size    Type     File system     Flags  
        32,3kB  1049kB  1016kB           Free Space  
 1      **1049kB**  536MB   535MB   primary  linux-swap(v1)  
        536MB   **1342MB**  806MB            Free Space  
  
Una vez deshabilitada borramos la partición:  
  
**sudo parted /dev/sdj rm 1**  
  
Creamos una nueva partición incluyendo el sistema de ficheros con:  
  

**sudo parted /dev/sdj mkpart primary linux-swap 1049kB 1342MB**

  
Comprobamos como queda la particion:  
  
**sudo parted /dev/sdj print free**  
  
Model: ATA VBOX HARDDISK (scsi)  
Disk /dev/sdj: 1342MB  
Sector size (logical/physical): 512B/512B  
Partition Table: msdos  
  
Number  Start   End     Size    Type     File system     Flags  
        32,3kB  1049kB  1016kB           Free Space  
 1      **1049kB  1342MB**  1341MB  primary  linux-swap(v1)  
  
**sudo fdisk -l /dev/sdj**  
  
Disk /dev/sdj: 1342 MB, 1342177280 bytes  
46 heads, 10 sectors/track, 5698 cylinders  
Units = cylinders of 460 \* 512 = 235520 bytes  
Sector size (logical/physical): 512 bytes / 512 bytes  
I/O size (minimum/optimal): 512 bytes / 512 bytes  
Disk identifier: 0x000d99d3  
  
   Device Boot      Start         End      Blocks   Id  System  
**/dev/sdj1**               5        5699     1309696   82  Linux swap / Solaris  
  
Generamos la swap:  
  
**sudo mkswap /dev/sdj1**  
  
Setting up swapspace version 1, size = 1309692 KiB  
no label, UUID=**7c7cfafe-03b2-4340-9ed3-3bef3a2be6b7**  
  
Esto genera un nuevo UUID:  
  
**ls -l /dev/disk/by-uuid/**  
  
lrwxrwxrwx 1 root root 10 ago 26 10:18 **7c7cfafe-03b2-4340-9ed3-3bef3a2be6b7** -> ../../sdj1  
  
Tras esto debemos actualizar la entrada para la swap del fichero "fstab" en /etc:  
  
**sudo vi /etc/fstab**  
  
\# swap was on /dev/sdj1 during installation  
UUID=**7c7cfafe-03b2-4340-9ed3-3bef3a2be6b7** none            swap    sw              0       0  
  
Una vez actualizado el fichero podemos reactivar la swap y ver como queda:  
  
**sudo swapon -a**  
  
**free**  
  
             total       used       free     shared    buffers     cached  
Mem:       1027264      66000     961264          0       6132      20704  
\-/+ buffers/cache:      39164     988100  
**Swap:      1309688          0    1309688**

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-4811916202838974906?l=tablondesastre.blogspot.com)

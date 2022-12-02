---

title: "Como redimensionar una partición ext4 sin perdida de datos"
date: "2011-08-19"
categories: 
  - "sin-categoria"
---

Este procedimiento es valido para puntos de montaje por decirlo de algún modo secundarios del sistema, por ejemplo el /srv.  
  
**df -h /srv**  
  
Filesystem            Size  Used Avail Use% Mounted on  
/dev/sdg1             123M  5,6M  111M   5% /srv  
  
Primero desmontamos el punto de montaje del dispositivo en el que se halla montado:  
  
**sudo umount /srv**  
  
Miramos como esta el asunto y nos anotamos los parámetros "Number" y "Start" de la partición a redimensionar y el parámetro "End" del espacio libre que nos queda:  
  
**sudo parted /dev/sdg print free**  
  
Model: ATA VBOX HARDDISK (scsi)  
Disk /dev/sdg: 2147MB  
Sector size (logical/physical): 512B/512B  
Partition Table: msdos  
  
Number  Start   End     Size    Type     File system  Flags  
        32,3kB  1049kB  1016kB           Free Space  
 **1**      **1049kB**  133MB   132MB   primary  ext4  
        133MB   **2147MB**  2014MB           Free Space  
  
Borramos la partición y la volvemos a crear usando los parámetros "Start" y "End" que hemos obtenido como referencia:  
  
**sudo parted /dev/sdg rm 1  
sudo parted /dev/sdg mkpart primary ext4 1049kB 2147MB**  
  
Volvemos a mirar como queda:  
  
**sudo parted /dev/sdg print free**  
  
Model: ATA VBOX HARDDISK (scsi)  
Disk /dev/sdg: 2147MB  
Sector size (logical/physical): 512B/512B  
Partition Table: msdos  
  
Number  Start   End     Size    Type     File system  Flags  
        32,3kB  1049kB  1016kB           Free Space  
 **1**      **1049kB**  **2147MB**  2146MB  primary  ext4  
  
Obtenemos los bloques de la nueva partición:  
  
**sudo fdisk -l /dev/sdg**  
  
Disk /dev/sdg: 2147 MB, 2147483648 bytes  
22 heads, 16 sectors/track, 11915 cylinders  
Units = cylinders of 352 \* 512 = 180224 bytes  
Sector size (logical/physical): 512 bytes / 512 bytes  
I/O size (minimum/optimal): 512 bytes / 512 bytes  
Disk identifier: 0x000486b3  
  
   Device Boot      Start         End      Blocks   Id  System  
/dev/sdg1               6       11916     **2096128**   83  Linux  
  
Chequeamos el sistema de ficheros:  
  
**sudo e2fsck -f /dev/sdg1**  
  
e2fsck 1.41.12 (17-May-2010)  
Pass 1: Checking inodes, blocks, and sizes  
Pass 2: Checking directory structure  
Pass 3: Checking directory connectivity  
Pass 4: Checking reference counts  
Pass 5: Checking group summary information  
/dev/sdg1: 15/516096 files (0.0% non-contiguous), 72236/2096128 blocks  
  
Expandimos el sistema de ficheros:  
  
**sudo resize2fs /dev/sdg1 2096128**  
  
resize2fs 1.41.12 (17-May-2010)  
Resizing the filesystem on /dev/sdg1 to 2096128 (1k) blocks.  
The filesystem on /dev/sdg1 is now 2096128 blocks long.  
  
Montamos el sistema de ficheros y miramos como queda:  
  
**sudo mount /dev/sdg1 /srv**  
  
**df -h /srv**  
  
Filesystem            Size  Used Avail Use% Mounted on  
/dev/sdg1             2,0G  7,0M  1,9G   1% /srv

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-5420305353998922872?l=tablondesastre.blogspot.com)

---
layout: posts
title: "Optimizando el NFSv4"
date: "2012-06-19"
categories: linux
---

## Dispositivos de bloques

Primero debemos parametrizar el fstab del servidor , aquí se montan por primera vez los dispositivos en el sistema.

Originariamente tenía:

UUID=5      /media/Ext4     ext4    user,rw    0       2

Y ahora tengo

UUID=5       /media/Ext4     ext4    user,rw,noatime,data=journal    0       2

data=journal tiene efectos positivos para ficheros que se leen y se escriben a la vez

Nota:

As quoted in the IBM doc "The results were astounding. data=journal mode allowed the 16-meg-file to be read from 9 to over 13 times faster than other ext3 modes, ReiserFS, and even ext2 (which has no journaling overhead): ... repeated this test, but tried to read a 16Mb file from the test filesystem (rather than a different filesystem), and he got identical results. So, what does this mean? Somehow, ext3's data=journal mode is incredibly well-suited to situations where data needs to be read from and written to disk at the same time. Therefore, ext3's data=journal mode, which was assumed to be the slowest of all ext3 modes in nearly all conditions, actually turns out to have a major performance advantage in busy environments where interactive IO performance needs to be maximized."

 Ahora los exports son montajes que debemos de retocar

/exports/Caso1   \*(sync,insecure,no\_subtree\_check,rw,nohide,no\_wdelay)

Se ha añadido el parámetro no\_wdelay y escritura síncrona con sync

## Servidor NFS

Ahora toca el servidor NFS , vamos a aumentar el numero de hilos que pueden escribir.

/etc/default/nfs-kernel-server

RPCNFSDCOUNT=128

**Configurar el TCP/IP**

/etc/sysctl.conf

net.core.rmem\_max = 16777216
net.core.wmem\_max = 16777216
net.ipv4.tcp\_rmem = 4096 87380 16777216
net.ipv4.tcp\_wmem = 4096 65535 16777216
net.core.netdev\_max\_backlog = 30000

FUENTES:

[https://www.ibm.com/developerworks/library/l-fs8/index.html](https://www.ibm.com/developerworks/library/l-fs8/index.html)

[https://www.mjmwired.net/kernel/Documentation/filesystems/ext3.txt](https://www.mjmwired.net/kernel/Documentation/filesystems/ext3.txt)

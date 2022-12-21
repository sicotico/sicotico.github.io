---
layout: post
title: "Preparando los recursos"
date: "2011-12-16"
categories: linux hardware
---

Lo primero es lo primero, manos a la obra con [fstab](https://help.ubuntu.com/community/Fstab "fstab") . Los parámetros utilizados son simples no backup y si a verificar los disco (0,1). Lo discos duros son accesibles

## NFSv4 server

Con los dispositivos montados en el sistema de ficheros , al método tradicional. Configuraremos el NFS y los recurso a exportar mediante el fichero export , nfs-kernel-server y nfs-commons. En este caso el NFSv4 requiere para su funcionamiento un _pseudo filesystem_ donde estén montados los recurso a compartir.

 mount --bin origen destino

Nota:

Este es el sistema que vamos a exportar

mkdir -p /exports/caso1

mkdir -p /exports/caso2

Vamos a cargar de contenido nuestro _pseudo filesystem_ , montado directorios reales en el.

mount --bind /media/aux1  /exports/caso1

mount --bind /media/aux2  /exports/caso2

En /etc/default/nfs-kernel-serverwe configuramos esto:

NEED\_SVCGSSD=no # no is default

En /etc/default/nfs-commonwe configuramos esto:

NEED\_IDMAPD=yes
NEED\_GSSD=no # no is default

Especificaremos las partes en las que queramos dividir nuestro sistema de ficheros a compartir.Marcamos un export grande , pero identificamos las diferentes partes en las que lo queremos dividir. Cada una con su segmento de red o equipo con permisos.

 /exports               \*(rw,sync,fsid=0,insecure,no\_subtree\_check)
 /exports/caso1  \*(rw,sync,nohide,insecure,no\_subtree\_check)
 /exports/caso2  \*(rw,sync,nohide,insecure,no\_subtree\_check)

Especial son el caso delos elementos menores ya que se les atribuye el parámetro `nohide`. Ahora podremos decidir que recurso montamos.

Como crear el _pseudo filesystem_ de NFS es un trabajo que queremos automatizar , utilizaremos el fstab para ello.

/media/aux1    /export/caso1   none    bind  0  0
/media/aux2    /export/caso2   none    bind  0  0

 

## NFS cliente

Ahora toca montar en el equipo cliente los recursos del NFS , un simple mount nos da acceso para realizar las pruebas

user@host:~$ sudo mount 172.1.1.21:/media/aux1 /media/caso1
mount: tipo fs incorrecto, opción incorrecta, superbloque incorrecto en 172.1.1.21:/media/caso1,
falta página de código o programa ayudante, u otro error
(para varios sistemas de archivos (ej. nfs, cifs) tal vez
necesite un /sbin/mount.<type> programa de ayuda)
En algunos casos se encuentra información en syslog, pruebe
dmesg | tail   o algo parecido

La primera en la frente , con este error tenemos que instalar `nfs-common`

sudo apt-get install nfs-common

Ahora ya podemos volver a intentar cargar y realizar la pruebas de permisos. Como estamos con NFSv4 no hay que especificar exports , de esta manera tendremos el directorio raíz con un solo montaje.

sudo mount -t nfs4 -o proto=tcp,port=2049 172.1.1.21:/ /media/server

Si todo es correcto debemos de fijar estos cambios como permanentes. Al inicio del sistema se monten los recursos NFS , para ello utilizaremos el fstab

172.1.1.21:/   /media/server   nfs4    rw,auto,user,sync,exec,proto=tcp,port=2049  0  0

Fuente: [NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto "NFSv4Howto") [Fstab](https://es.wikipedia.org/wiki/Fstab "Wikipedia mount") [Wikipedia](https://es.wikipedia.org/wiki/Fstab "Wikipedia mount")

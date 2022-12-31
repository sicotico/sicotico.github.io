---
layout: single
title: "FSCK un aliado"
date: "2011-09-25"
categories: linux
---

Esta herramienta de verificación de sistemas de ficheros es la estándar en sistemas Linux. Por defecto viene habilitada para ejecutar tras un numero de montajes , dejando una marca para ejecutarse en el siguiente reinicio.

Como se puede observar tiene una utilización preventiva , ya que se ejecuta con asiduidad. Nosotros podemos cambiar esos parámetros  o utilizarla de forma manual. Importante recopilar nuestra tabla de particiones , para ello utilizaremos

sudo fdisk -l
Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 \* 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00006d67

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   \*          26        7321    58593748   af  HFS / HFS+
/dev/sda3            7321        7819     3999744   82  swap
/dev/sda4            7819        9642    14648320   83  Linux

Replanificación de la verificaciones automáticas de nuestros sistemas de fichero , empezamos por saber la situación actual

sudo dumpe2fs -h /dev/sda1 | grep -i 'mount count'
dumpe2fs 1.41.14 (22-Dec-2010)
Mount count:              24
Maximum mount count:      33

Ahora reconfiguramos cada cuanto se verifican los discos. Utilizaremos dos unidades de media que serán el numero de montajes y el tiempo. El parámetro "-c" hace referencia al contador de montajes del sistema  y el parámetro "-i" al intervalo que ha de existir entre revisiones.

sudo tune2fs -c 10 -i 1m /dev/sda3

sudo tune2fs -c 10 -i 1m /dev/sda4

Con esto ya tenemos la verificación preventiva cada 10 montajes o 1 mes entre verificaciones.

Para utilizarlo de forma manual tiene un requisito indispensable hay que utilizar sistemas de ficheros desmontados. Esto acarrea que manualmente no podríamos verificar el sistema raíz , para ello lo que hacemos es marcarlo para que en el siguiente reinicio se verifique. Tenemos varios métodos para esta acción: Crear un fichero llamado forcefsck , obligatoriamente en "/"

#cd /
# touch /forcefsck
Ahora reiniciamos el sistema:
# sudo reboot
Frce fsck on next boot using shutdown command

Mediante el comando shutdown podemos indicar esta revisión utilizando el parámetro "-F"  , este sera ejecutado con sudo

\# sudo shutdown -rF now

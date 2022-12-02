---

title: "GPT - Regenerar backup"
date: "2013-12-30"
categories: 
  - "sin-categoria"
---

## GPT ese gran desconocido

 

\[box type="info"\] GPT o Tabla de partición GUID \[/box\]

Lo primero una introducción para el que ha llegado aquí sin saber lo que buscaba , vamos como yo hace unos días.

Los discos duros poseen un tabla de particiones , antiguamente referenciado por el MBR , ahora es algo más complejo  para dar cabida al sistema EFI y a las grandes capacidades de almacenamiento. Yo lo descubrí por comprarme un disco de 3TB . Sigue existiendo el MBR para proporciona retrocompatibilidad.

![GPT esquema](https://upload.wikimedia.org/wikipedia/commons/0/07/GUID_Partition_Table_Scheme.svg)

Después de meses utilizando el disco decido redimensionar las particiones  y me encuentro con un error al arrancar el  GParted.

\[box type="warning"\] ¡ dios voy a perder todos los datos !\[/box\]

Puff , he tenido suerte  , GPT utiliza dos tablas particiones , una de copia de seguridad. Pues no se como pero me he quedado sin backup  , esta corrupto.

La solución pasa por reconstruir el backup en base  de la tabla primaria.  La verdad es que suena como algo "super técnico" , pero solo necesitamos la primera piedra.

Nuestro punto de inicio es la aplicación gdisik  , según el man  un manipulador de tablas GPT.

 gdisk /dev/sdXX

Command (? for help): ?
b	back up GPT data to a file
c	change a partitions name
d	delete a partition
i	show detailed information on a partition
l	list known partition types
n	add a new partition
o	create a new empty GUID partition table (GPT)
p	print the partition table
q	quit without saving changes
r	recovery and transformation options (experts only)
s	sort partitions
t	change a partition's type code
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Command (? for help): r

Recovery/transformation command (? for help): ?
b	use backup GPT header (rebuilding main)
c	load backup partition table from disk (rebuilding main)
d	use main GPT header (rebuilding backup)
e	load main partition table from disk (rebuilding backup)
f	load MBR and build fresh GPT from it
g	convert GPT into MBR and exit
h	make hybrid MBR
i	show detailed information on a partition
l	load partition data from a backup file
m	return to main menu
o	print protective MBR data
p	print the partition table
q	quit without saving changes
t	transform BSD disklabel partition
v	verify disk
w	write table to disk and exit
x	extra functionality (experts only)
?	print this menu

Recovery/transformation command (? for help): d

Utilizamos la  "?" para ver el menú , seleccionamos:

r    recovery and transformation options (experts only)

volvemos a utilizar la  "?" para ver el menú y seleccionamos:

d    use main GPT header (rebuilding backup)

 

### Fuentes:

[Tabla de particiones GUID](https://es.wikipedia.org/wiki/Tabla_de_particiones_GUID "Tabla de particiones GUID")

[Gdisk - reparaciones de GPT](https://www.rodsbooks.com/gdisk/repairing.html "gdisk repararciones")

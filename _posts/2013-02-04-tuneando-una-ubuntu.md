---
layout: post
title: "Tuneando una Ubuntu"
date: "2013-02-04"
categories: linux
---

"Tuneando" que concepto tan relacionado a los coches , pero muy utilizado en informática

Para tunear una Ubuntu o cualquiera maquina/software hay que tener clara la idea principal y en este caso es:

\[box\] **No me des potencia , quítame peso**

Frase atribuida a Sir Colin Chapman\[/box\]

Ahora queda clara la postura principal y todo el objetivo será reducir peso de Unity en una Ubuntu 12.04 LTS.

Dividiremos en dos partes este proceso. Uno lo dedicaremos a parámetros del sistema operativo y algún software que nos ayude. en la segund aparte iremos por el peso del sistema , desinstalar aplicaciones que no usamos y otras que no sabíamos que estaban ahí

## Tuneando el sistema

### Reducir el uso de la paginación.

Para este punto hay dos formas de hacerlo , la de toda la vida  , priorizar en sysctl el uso de RAM  o este método basado software en redirigir las páginas a un dispositivo de bloques comprimidos en memoria. El segundo método es más completo pero añade software y un acapa de gestión , tiene como punto fuerte equipos con poca memoria RAM.

[Configurar sysctl](https://luispuente.net/2010/01/reducir-el-uso-de-swap/ "Reducir el uso de swap")

Software de gestión de RAM

`~$ sudo add-apt-repository ppa:shnatsel/zram ~$ sudo apt-get update ~$ sudo apt-get install zramswap-enabler ~$ sudo start zramswap`

 

Desinstalación del Software de gestión de RAM

`~$ sudo apt-get remove --purge preload zramswap-enabler`

 

### Mover /tmp a RAM

Con este paso buscamos mejorar la escritura de diferentes en esta carpeta.  Solo se puede realizar si tu uso de RAM esta bastante por debajo de total de tu equipo.

`tmpfs /tmp tmpfs defaults,noexec,nosuid 0 0`

 

### Deshabilitar efecto gráficos

Necesitaremos de una herramienta externa , **_Compizconfig Settings Manager_ .** Muy posiblemente  ya la tengáis instalada **,** aquí deshabilitaremos todos los efectos salvo la decoración de ventas. este "Efecto" es la barra superior donde se encuentra el título y los 3 botones.

![](images/8933173527_24424e6afa_b.jpg)

### Usemos todos los cores para el inicio del sistema

Queremos sacar el máximo partido a los cores de nuestra CPU , o  Cores Virtuales si tenemos  Hyper Threading. Debemos de configurar un parámetro en  el inicio del sistema  **init.d**

_/etc/init./rc_

_Cadena buscar_

**CONCURRENCY=none**

_Cadena nueva_

**CONCURRENCY=makefile**

 

### Menos servicios mejor.

\[caption id="" align="aligncenter" width="640"\]![Tuneando Ubuntu BootUp-Manager](images/8436348902_ba994b8933_z.jpg "BootUp-Manager") BootUp-Manager\[/caption\]

Aquí debemos de parar los servicios que no usemos , mas de una vez tenemos algún MySQL o Apache funcionando sin saberlo. Esta tarea es extremadamente fácil. Simplemente necesitamos instalar un programa que nos deje gestionarlo. Sencillo fácil y para toda la familia no es fácil. Yo he elegido [BootUp Manager](https://www.marzocca.net/linux/bum.html "BootUp-Manager")

\[caption id="" align="aligncenter" width="640"\]![Tuneando Ubuntu BootUp-Manager](images/8435262763_403992e36a_z.jpg "BootUp-Manager") BootUp-Manager\[/caption\]

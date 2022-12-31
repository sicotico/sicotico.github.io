---
layout: single
title: "Servicios en HP-UX"
date: "2011-01-21"
categories: linux
---

## Crear un servicio en HP-UX

Crear un fichero en `/sbin/init.d` con este formato , es lo básico.

unset UNIX95
PATH=/sbin:/usr/sbin:/usr/bin:/usr/lib/netsvc:/usr/lib/netsvc/yp
export PATH

rval=0

case $1 in
start\_msg)
           echo "Mensaje de arranque del servicio"
           ;;

stop\_msg)
           echo "Mensaje de parada del servicio"
           ;;

start)
            Ruta absoluta del script o ejecutable de inicio
            ;;
stop)
            Ruta absoluta del script o ejecutable de inicio
            ;;
\*)
echo "usage: $0 {start|stop}"
;;
esac

exit $rval

Lo básico de los servicios es que han de estar en la carpeta /sbin/rcX.d/ para iniciarse. Hay que seguir unas normas de nombrado delos ficheros de esta carpeta.

Los ficheros empiezan por S o K si queremos arrancarlo o pararlo

Insertar un numero en el nombre el cual indica cuando se va a ejecutar  ,  el menor numero sera el primero en iniciarse.

Ahora ponemos el nombre identificativo.

El resultado final seria algo cercano a esto :

- `/sbin/rc3.d/S99nfs` -> inicia el servicio
- `/sbin/rc2.d/K99nfs` -> para el servicio

Ahora creamos los enlaces simbólicos a los runlevel necesarios para nuestra aplicación , lo haremos en el runlevel 3 para iniciar y 2 para apagar.

ln -s /sbin/init.d/nfs /sbin/rc3.d/S99nfs

ln -s /sbin/init.d/nfs /sbin/rc2.d/K99nfs

## Arranque y parada

Esto es mucho más sencillo

- `/sbin/init.d/nombre_servicio start`
- `/sbin/init.d/nombre_servicio stop`

## Edita inittab

En este fichero cada linea representa un servicio , la sintaxis esta definida mediante una separación por ":" de cada atributo.

Esto seria a nivel global:

_Etiqueta:comportamiento:runlevel:ejecutable y parámetros de salida_

- _Etiqueta_ 4 caracteres que nos ayuden a recordar que significa ese servicio
- _Comportamiento_ aquí con determinadas palabras de sistema definiremos como queremos que se comporte el servicio.

> - _initdefault_ marca el nivel de ejecución
> - _wait_ hasta que no termine este servicio no arrancamos el siguiente
> - _boot_ solo lo inicia en arranque de maquina
> - _bootwait_ una combinación de Boot y wait
> - _respawn_ re relanza el proceso de forma automática si muere

- _Runlevel_ aquí indicamos los runlevel donde queremos que se ejecute el servicio , se pueden poner varios
- Ahora toca poner lo que queremos ejecutar y los parámetros de salida nos derivaran los mensajes a donde queramos , yo utilizo > /dev/console 2>1$

Nota:

El fichero `inittab` tiene como función levantar los servicios primarios del sistema , asi que no hes nada recomendable poner ahí servicios. Si lo hiciéramos perderíamos la interfaz de administración de servicios `{start|stop|status}` que nos brinda los rcX

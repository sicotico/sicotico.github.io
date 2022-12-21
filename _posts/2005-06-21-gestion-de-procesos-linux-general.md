---
layout: post
title: "Gestion de procesos (Linux general)"
date: "2005-06-21"
categories: 
  - "sin-categoria"
---

Un proceso es cualquier instrucción o programa que en ese momento se está ejecutando en nuestro sistema. Todo proceso tiene un PID (Process IDentifier), es decir, un número que le identifica y le diferencia de todos los demás. Una característa importante es que todo proceso tiene un estado: corriendo, durmiendo, zombie o parado.

El comando kill

El comando kill nos permite interactuar con cualquier proceso mandando señales (signal). Cuando ejecutamos kill pid lo que hacemos es mandar la señal de TERM(terminar) con lo cual se termina ese proceso. Podemos usar cualquier otro tipo de señal, para ello utilizamos kill signal pid. Podemos conseguir una lista de señales usando kill -l. Una señal útil para alunas ocasiones es -9, esta señal fuerza a terminar cualquier proceso. Como su nombre indica, estamos matando el proceso.

También podemos utilizar el comando killall con el que podemos mandar señales a un proceso utilizando el nombre, en vez del PID.

Entre los procesos diferenciamos los que se están ejecuntando en 1er o 2o plano. Los que se ejecutan en primer plano son los que interactúan con el usuario en ese momento, mientras que los procesos en segundo plano se ejecutan pero están ocultos, y muy posiblemente el usuario no tenga constancia de que se esté ejecutando. Sólo puede haber un proceso en primer plano por consola. Eso nos deja las manos atadas si no estamos en el entorno gráfico. Para poder ejecutar varios comandos, lo que podemos hacer es ejecutar los comandos en segundo plano. Para ello solo tenemos que añadir & al final del comando. Vamos a poner un ejemplo:

$ls -R / > /dev/null &

En el anterior ejemplo listamos todos los ficheros de todos los directorios del sistema. Enviamos la salida a /dev/null para que su salida no nos moleste. El carácter & manda el proceso a segundo plano. El comando jobs nos muestra los procesos que se están ejecutando en segundo plano:

$ls \[1\]+ Running ls --color -R / >/dev/null &

Aquí estamos ejecutando el comando anterior. El elemento \[1\] nos indica el número del proceso que se están ejecutando en segundo plano y cuál es su estado. En este caso Running(corriendo). Seguidamente nos muestra cuál es el proceso Podemos utilizar también el comando fg para mandar un proceso al primer plano y el comando bg para mandar el proceso al segundo plano.

$fg ls --color -R / >/dev/null

fg manda el proceso al primer plano y nos muestra el programa que ha mandado. Si tenemos varios procesos en segundo plano añadimos el número del proceso.

El comando bg se utiliza cuando tenemos, por ejemplo, procesos suspendidos. Estos procesos son programas que están parados, es decir, no consumen ni CPU ni memoria, y que podemos volver a poner en archa en cualquier momento. Para suspender un proceso utilizamos la combinación de teclas Ctrl-z, al igual que para interrumpir un proceso utilizamos Ctrl-c.

$jobs \[1\]+ Stopped ls --color -R / >/dev/null

Esta tarea está parada(Stopped).

El comando ps

El comando ps permite mostrar todos los procesos que están corriendo en nuestro sistema. Veamos una parte de una salida del comando ps:

$ps -aux faraox@menut:~/doc/glup\_0.6-1.1-html-1.1$ ps xau USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND root 1 0.0 0.2 1272 436 ? S 16:00 0:04 init \[2\] root 2 0.0 0.0 0 0 ? SW 16:00 0:01 \[keventd\] root 3 0.0 0.0 0 0 ? SW 16:00 0:00 \[kapmd\] faraox 1363 0.0 0.8 2740 1564 pts/2 S 18:57 0:00 -bash

Los parámetros xau nos permiten ver todos los procesos que se están ejecutando. El parámetro a muestra lo que se está ejecutando en las tty conocidas, el parámetro x añade los procesos que no se conece la tty en la que se están ejecutando y u muestra los usuarios que están ejecutando esos procesos.

Algunas partes de la salida le serán conocidas. La columna USER nos dice que usuario está ejecutando el proceso,PID es su número de proceso, %CPU es el porcentaje de CPU que está utilizando al igual que %MEM es el porcentaje de memoria. También incluye la cantidad de memoria en kylobytes que ha utilizado dicho proceso, se muestra en la columan RSS.La columna TTY muestra la consola desde la que se está ejecutando. STAT nos muestra el estado del proceso:S(drmiendo), R(corriendo), T(parado), Z(zombie). Las opciones W y N son especiales para procesos del kernel. La columna START muestra la hora a la que empezó el proceso, y la columna TIME muestra el tiempo de CPU que ha usado el proceso desde que se inició y COMMAND muestra el nombre del comando que se está ejecutando.

El comando top

El comando top es una utilidad que permite la monitorización de los procesos de la CPU. También muestra el estado de la memoria. Es una mezcla del comando uptime, free y ps.

20:07:54 up 4:07, 5 users, load average: 0.07, 0.05, 0.05 60 processes: 58 sleeping, 1 running, 0 zombie, 1 stopped CPU states: 0.4% user, 0.6% system, 0.0% nice, 99.0% idle Mem: 182900K total, 172404K used, 10496K free, 35064K buffers Swap: 96352K total, 14284K used, 82068K free, 43228K cached

PID USER PRI NI SIZE RSS SHARE STAT %CPU %MEM TIME COMMAND 1565 faraox 14 0 1040 1040 820 R 0.5 0.5 0:00 top 300 root 9 -10 24736 9.9M 1524 S

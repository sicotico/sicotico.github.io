---
layout: single
title: "Lanzar aplicaciones graficas en equipos remotos por ssh"
date: "2008-03-14"
categories: linux
---

Lo que queremos hacer implica escribir en el display de la máquina destino. Eso se hace de la siguiente manera.

Inicias sesión SSH en la maquina donde quieres correr la aplicación. Por una cuestión de seguridad, asegúrate de iniciar sesión con el mismo usuario que tiene sesión abierta en la máquina remota.

Una vez que estás logueado, tienes que definir una variable de entorno DISPLAY que apunte al display local.Por ejemplo, quiero correr en la otra máquina la calculadora.Debe de existir una sesión X iniciado con el mismo usuario con el que nos hemos logueado.

Nota:

Para la conexión podemos usar ssh -l "username" host o ssh username@host

Ahora, necesito saber cual es el servidor, al que me voy a conectar. Casi siempre hay solo uno, por lo que uso el 0. Para decirle a los programas que voy a correr cual es servidor X al que deben enviar las salidas, uso la variable. DISPLAY. En este ejemplo supongo que estás usando bash.

$ export DISPLAY=:0.0

con eso ya definí una variable de ambiente o entorno que todos los programas pensados para X buscan al arrancar. ahora ejecuto el programa.

Ejecuta una aplicación gráfica y veras su salida por consola y la venta aparecerá en la pantalla del usuario con mismo "username" identificado en el servidor X

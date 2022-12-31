---
layout: single
title: "Poner a Español Slack\" Esposible !!! \""
date: "2004-11-12"
categories: linux
---

### [](https://sicotico.blogspot.com/2004/11/poner-espaol-slack-esposible.html)

Bueno al arrancar viene en Ingles pero eso se puede solucionar , tal y como funciona linux es se configura en función de unas variables las cuales modificamos en una consola temporalmente para alguna acción por medio de export . En el arranque se cargan y esta en algún fichero , por supuesto el fichero esta en /etc/ todo esta aquí siempre ,xdddd . Pues ahora se trata de modificar una o dos variables , la que nos interesa es $LANG , si esta variable es igual a es\_ES el sistema seleccionara para todos los programas el español , en base al estándar i18-n que no es mas que una colección de ficheros de texto donde se escriben todos los texto de los programas y así es mas fácil de intercambian lenguajes , en nuestro caso es el es\_ES@Euro . en /etc/profile ( intuitivo , el lenguaje se cambiar el el perfil del sistema , " profile.d" ) hay varios scripts y el que nos interesa esta relacionado con lang , así que buscamos uno que se parezca y lo editamos con pico nano vi , el que nos guste . Dentro tendremos las variable $LANG para modificar. Después salimos guardando y reiniciamos el sistema , es la forma más segura porque ejecutando source profile no me ha funcionado nunca completamente .

A partir de ahora todos los programas que haya i18n en español serán seleccionados incluso si bajamos el man es español también solo que habrá que modificar algo para ver nuestra tan añorada "ñ"

Bueno esto es todo esto es todo totototo todo amigos....

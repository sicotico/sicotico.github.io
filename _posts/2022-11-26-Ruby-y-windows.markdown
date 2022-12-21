---
layout: post
title:  "Ruby y windows"
date:   2023-11-26 10:57:08 +0200
categories: jekyll
---


Hay cosas que es mejor no hacer.

Aclaro mejor el entorno donde empecé fue un Windows 10 con vscode y lo uso más para analizar JSON y biceps que para desarrollar. 

Viendo que habia compatibilidad en windows pues me tiré a la piscina para terminar lo antes posible. Ya de entrada necesitabas un paquete especial,el Ruby+Devkit, ejecutar ridk y terminales MINGW. Esto no me alerto de la instalación ta sucia que conllevaba.

---
* Ruby y devkit en el raiz
* las gemas de jekyll y bundler a nivel SO
* Lo tiempo de la varaiable path
---

En este punto empce con la migración de contenido , extraer los post de Wordpres en formato markdown parecia facil , hay un script para esta tarea. Tuve mala suerte con la gema de mysql y no la detectaba a nivel de SO ni ejecutando un entorno de bundler para la migración. Siempre hay un plan B y en este caso fué un plugin en wordpress !(Jekyll Exporter)[https://wordpress.org/plugins/jekyll-exporter/], con el obtenemos un zip con todos los articulos en fichero markdown separados y listos para incluir en la carpeta "_posts". El problema descrito en 4 lineas me llevo 4 días, es lo qu tiene no tener ni idea del entorno Ruby.

Con un entorno local funcionado ya nos ponemos manos a la obra con el nueblo blog estático. Segun creo el poyecto  lo veo funcionado con los post, al crear el proyecto se genea con el tema  minima. Que resuena en tu cabeza, ya está casi hecho, a buscar un tema molon como los de wordpres que tiene panel de copntrol y se configuran en nada. Si he escrito esto para que el que lo lea se ria un rato, obviamente no salio el plan así. Haber alma de cantaro  y es contenido estático un poco listo, donde va haber un panel de gestión. Primer tema y veo la configuración por ficheros , y que eso no terminaba , ya no me acuerdo el numero de lineas pero me dio mareos. Meditar  no puede ser tandificil  editar el tema de minima para dejarlo bonito. Cambio de rumbo, hey que soy Scrum Master, sprint nuevo despues de haber hablado con los interesados, mis otras personalidades. 

Sprint 2 - Tema minima- Tampoco salio, bueno funcionar funcionaba a veces, como que a veces y si lo subia git se rombia o no se parecia al local. Dias leyendo a rato, borando cache del servidor jekyll , modificando plantillas , probando temas en gema  y en remoto. Ninguan mejora , todos los errores y los fallos del estilo eran aleatorios.

Sprint 3 - Borrar y volver a empezar. 
* Borro todos los ficheros (salvo la carpeta post 
* Aplico cambios al git
* Limmpio la gemas del sistema
* Genero nuevo bundler 
* Genero proyecto
* Cargo los post 
* Pruebo en local y todo perfecto con el tema basico
* Lo subo a git y perfecto

Ya no lo toco unas semans para aclarame las ideas


Sprint 3 - Nuevo tema 100% compatible con GitPages - Aqui pues que contar, no hay por donde cogerlo. Un tema precioso y con una web super documentado , pero oye que no lo entendía. Unos dias mirando a ratos y tiene 3 estructuras completas. La que carga por defecto esta casi vacia, hay una carpeta con lo mismo  mas datos de ejemplo  y otro con  más contenido aun que es la de la doc. Toda una gran novela al estilo del señor de los anillos.

Sprint 4 - Vuelta alas modifiaciones - Ahora tenia el pecho hinchado, esto lo hago yo en un rato,  pues nada al tajo. Mismo problema los cambios no se ven siempre  , el parameetro --incremetal del servidor de jeckyll no funciona y empieza la deseperación. Esta vez con golpe de suerte , cierro el cmd de jekyll y lo vuelvo abrir cargo el server  y veo todos los cambio funcioanndo. Pues sí el cmd o powerShell de Windows 10 se atasca y no da error con el servidor de Jekyll. He de decir que no lo he solucionado, simplemente he cambiado mi rutina de trabajo y cuando tengo un hueco para el siguiente sprint lo instalré en el WSL y veré si ahí me funciona mejor. Eso espero, asi puedo eliminar todo el Ruby de mi equipo.



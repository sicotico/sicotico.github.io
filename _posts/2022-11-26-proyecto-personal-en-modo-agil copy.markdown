---
layout: single
title:  "Proyecto personal en modo ágil"
date:   2023-11-26 10:57:08 +0200
categories: jekyll
---

Hay cosas que es mejor no hacer.

Aclaro mejor el entorno donde empecé fue un Windows 10 con vscode y lo uso más para analizar JSON y biceps que para desarrollar. 

Viendo que habia compatibilidad en windows pues me tiré a la piscina para terminar lo antes posible. Ya de entrada necesitabas un paquete especial,el Ruby+Devkit, ejecutar ridk y terminales MINGW. Esto no me alerto de la instalación ta sucia que conllevaba.

---
* Ruby y devkit en el raíz
* las gemas de jekyll y bundler a nivel SO
* Lo tiempo de la variable path
---

Hey que soy Scrum Master, sprint nuevo después de haber hablado con los interesados, mis otras personalidades. 

__Sprint 1__
El entorno local lo cree en el post [Aventuras de WordPress a Jekyll](2022-11-02-aventuras-de-WordPress-a-Jekyll.markdown)

__Sprint 2__

En este punto empece con la migración de contenido, extraer los post de WordPress en formato markdown parecía fácil, hay un script para esta tarea. Tuve mala suerte con la gema de mysql y no la detectaba a nivel de SO ni ejecutando un entorno de bundler para la migración. Siempre hay un plan B y en este caso fué un plugin en WordPress !(Jekyll Exporter)[https://wordpress.org/plugins/jekyll-exporter/], con el obtenemos un zip con todos los artículos en fichero markdown separados y listos para incluir en la carpeta "_posts". El problema descrito en 4 lineas me llevo 4 días, es lo qu tiene no tener ni idea del entorno Ruby.

__Sprint 3__  

Con un entorno local funcionado ya nos ponemos manos a la obra con el nuevo blog estático. Según creo el proyecto lo veo funcionado, añadir los post es simplemente crear una carpeta con el contenido el resultado del plugin de WordPress, al crear el proyecto se genera con el tema  _minima_. Que resuena en tu cabeza, ya está casi hecho, a buscar un tema molón como los de WordPress que tiene panel de control y se configuran en nada. Si he escrito esto para que el que lo lea se ria un rato, obviamente no salio el plan así. Haber alma de cántaro y es contenido estático un poco listo, donde va haber un panel de gestión. Primer tema y veo la configuración por ficheros (eso no terminaba nunca), ya no me acuerdo el numero de lineas pero me dio mareos. Meditar no puede ser tan difícil editar el tema de _minima_ para dejarlo bonito. Cambio de rumbo. 

__Sprint 4__  

Tema _minima_- Tampoco salio, bueno funcionar funcionaba a veces, como que a veces y si lo subía git se rompía o no se parecía al local. Días leyendo a rato, borrando cache del servidor jekyll , modificando plantillas, probando temas en gema  y en remoto. Ninguna mejora , todos los errores y los fallos del estilo eran aleatorios.

__Sprint 5__  

Borrar y volver a empezar. 
* Borro todos los ficheros (salvo la carpeta post 
* Aplico cambios al git
* Limpio la gemas del sistema
* Genero nuevo bundler 
* Genero proyecto
* Cargo los post 
* Pruebo en local y todo perfecto con el tema básico
* Lo subo a git y perfecto

Ya no lo toco unas semanas para aclárame las ideas

__Sprint 6__  

Nuevo tema 100% compatible con GitPages - Aquí pues que contar, no hay por donde cogerlo. Un tema precioso y con una web super documentado, pero oye que no lo entendía. Unos días mirando a ratos y tiene 3 estructuras completas. La que carga por defecto esta casi vacía, hay una carpeta con lo mismo  mas datos de ejemplo  y otro con  más contenido aun que es la de la doc. Toda una gran novela al estilo del señor de los anillos.

__Sprint 7__  

Vuelta a las modificaciones - Ahora tenia el pecho hinchado, esto lo hago yo en un rato,  pues nada al tajo. Mismo problema los cambios no se ven siempre, el parámetro --incremetal del servidor de jeckyll no funciona y empieza la desesperación. Esta vez con golpe de suerte , cierro el cmd de jekyll y lo vuelvo abrir cargo el server  y veo todos los cambio funcionando. Pues sí el cmd o powerShell de Windows 10 se atasca y no da error con el servidor de Jekyll. He de decir que no lo he solucionado, simplemente he cambiado mi rutina de trabajo y cuando tengo un hueco para el siguiente sprint lo instalaré en el WSL y veré si ahí me funciona mejor. Eso espero, asi puedo eliminar todo el Ruby de mi equipo.


__Sprint 8__ 

Cambiar dominio a Git-Pages
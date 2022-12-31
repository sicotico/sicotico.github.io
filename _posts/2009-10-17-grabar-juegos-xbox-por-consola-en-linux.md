---
layout: single
title: "Grabar juegos xbox por consola en Linux"
date: "2009-10-17"
categories: hardware
---

Mi novia está enganchada a la batería de la xbox y se ha bajado unos cuantos juegos para ir practicando. El problema es que nunca se acuerda del comando por consola para grabarlo en linux (yo tampoco que conste), y los interface gráficos son para débiles (Luismi dixit) así que ahí va Lole, y grábame todos los juegos para que yo también pueda jugar!!!

Instrucciones:

- `-speed=2 , marcamos la velocidad`
- `/dev/hdc , es la dirección de la grabadora`

`growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/hdc=<nombre de la iso>`

Fuente: [www.elotrolado.net](https://www.elotrolado.net/hilo_grabar-juegos-xbox-360-en-linux_856404)

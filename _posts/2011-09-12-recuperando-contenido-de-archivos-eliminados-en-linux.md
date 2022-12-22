---
layout: posts
title: "Recuperando contenido de archivos eliminados en Linux"
date: "2011-09-12"
categories: linux
---

Es la segunda vez en mi vida que cometo el error de eliminar un archivo usando **rm** o **mv** en la línea de comandos. La otra vez que me pasó, conseguí recuperar el archivo de texto (que era un programa enorme). Estoy ahora mismo en el proceso de recuperar mi segundo archivo.

sudo grep -i -a -B50 -A100 'yellowpages' /dev/sda1 > raw.txt

El comando de arriba busca en toda la partición `/dev/sda1` la palabra yellowpages (porque en mi caso era una palabra que utilizaba en el programa)  y devuelve las 50 líneas anteriores a la palabra y las 100 líneas posteriores. Es una estimación del tamaño de mi programa.

Antes de ejecutar el comando, asegúrate de cuál es la partición en la que estaba el archivo que quieres recuperar, por ejemplo con

sudo fdisk -l

Piensa en una palabra rara que usaras en el programa (en mi caso yellowpages) y a esperar hasta que termine de llenarse el archivo “raw.txt”. Cuando termine, puedes tranquilamente buscar el contenido de tu archivo de texto en su interior.

---
layout: single
title: "Objetos y Arrays en JavaScript"
date: "2010-05-13"
categories: dev
---

Siguiendo con la programación de la API de Google Maps en JavaScript me he encontrado con mucho código y con unas ganas tremendas de convertirlo POO , es bueno practicar y no olvidar estos conocimientos.

Estoy solventando un problema de indefinidos puntos y estos con sus coordenada y direcciones , la idea se me ha ocurrido mientras comía así que espero no haber liado ensaladas de queso con un par de instancias.

Lo primero es crear un array , este puede ser de longitud fija o variable , yo he utilizado variables

var "nombre de variable" = new Array();

Para 10 elementos : var "nombre de variable" = new Array(10);

Ahora definimos los objetos en JS , al buscar documentación me que d sorprendido de la simpleza con la que lo han implementado. Solo tenemos que crear un función a modo de constructor

function pos(nombre, coordenadas, code, request) {

  this.nombre = nombre

  this.coordenadas = coordenadas

  this.code = code

  this.request = request

  this.acuracy = acuracy

}

Pues Bien , aparte de poder organizarlo con metodología  POO , aquí atender las necesidades de un objeto , como son su métodos.  En este caso  la política a seguir es un poco diferente. Primero creamos funciones y después las incluimos en nuestras definiciones de objetos.  La flexibilidad que nos aportar es poder compartir el código para funciones de llamada inmediata.

function mostrartexto(texto) {
  this.texto= texto
}
function pos(nombre, coordenadas, code, request, acuracy) {

  this.nombre = nombre

  this.coordenadas = coordenadas

  this.code = code

  this.request = request

  this.acuracy = acuracy

  this.texto = mostrartexto("Hola Mundo!")
}

Esto es todo por ahora , según avancemos más anotaremos...

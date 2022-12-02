---

title: "Cadenas en Batch"
date: "2010-05-20"
categories: 
  - "sin-categoria"
---

## Recortar cadenas

### por el final

Este código recorta la variable desde el final al principio , según el parámetro **\-5%**

@ECHO OFF
SET cadena=CALIFRAJILISTICO
SET cadena=%cadena:~0,-5%
IF "%cadena%" == "CALIFRAJILI" GOTO BIEN

:MAL
     ECHO MAL
     EXIT /B 1
:BIEN
     ECHO BIEN
     EXIT /B 1

### Por el principio

Este código recorta la variable desde el final al principio , según el parámetro **-5%**

@ECHO OFF
SET cadena=CALIFRAJILISTICO
SET cadena=%cadena:~,-5%
IF "%cadena%" == "RAJILISTICO" GOTO BIEN

:MAL
     ECHO MAL
     EXIT /B 1
:BIEN
     ECHO BIEN
     EXIT /B 1

### Concepto

La combinacion 0~ es la que proporciona le acceso al final de la cadena , como solamente con ~ nos posiciona al principio

## Sustituir caracteres dentro de cadenas

    set variable=+jeje+123

Basándonos en la cadena anterior vamos a sustituir **todos** los signos "+" por las letras "P". En ese caso hacemos a continuación:

    set variable=%variable:+=P%

En este caso, al ejecutar ahora un `echo %variable%` nos devolverá: **"PjejeP123"**

Podemos normalizar numeros eliminando los signo de puntuación

    set variable=8.983.450.567

si hacemos ahora:

    set variable=%variable:.=%

El resultado sera **"8983450567"**

### Documentación básica

[Batch en Wikipedia](https://es.wikipedia.org/wiki/Batch)

[elhacker.net](https://foro.elhacker.net/scripting/programacion_batch_avanzada_nuevo-t132924.0.html)

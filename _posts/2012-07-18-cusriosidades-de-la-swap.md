---

title: "Cusriosidades de la swap"
date: "2012-07-18"
categories: 
  - "sin-categoria"
---

Un par de conceptos básico que siempre que instalo el sistema s eme olvida como se configura.

## Política de uso

Tenemos la capacidad de decidir si queremos que se use la swap de una manera agresiva o solo en el casa extremo de necesidad

_swappiness = 0_ indica al núcleo evitar el intercambio de procesos de la memoria física durante el tiempo que sea posible _swappiness = 100_ indica al núcleo la utilización  agresivamente de intercambio de procesos de la memoria física y mover los para intercambiar caché

## Ampliar la swap

Por supuesto que **no**. Con el kernel 2.6, "un archivo de intercambio es tan rápido como una partición de intercambio

Fuentes:

[Ubuntu Community](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

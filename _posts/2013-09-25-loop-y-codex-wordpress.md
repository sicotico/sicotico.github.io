---
layout: posts
title: "Loop y Codex Wordpress"
date: "2013-09-25"
categories: dev
---

## Loop ordenado

Hoy he tenido que modificar el orden en el que muestra los datos un Loop. Es bastante sencillo cuando entiendes su funcionamiento. Recopilo los recursos que he utilizado y las dos forma de estructurar el código para obtener el mismo efecto.

\[box\] En WordPress el Loop es toda una institución , posee un serie de objetos en la API para abstraerte de las consultas SQL.\[/box\]

Lo más **correcto** es utilizar [WP\_Query](codex.wordpress.org/Class_Reference/WP_Query "codex WP_Query")

El código esta generado mediante arrays , este contiene todos los parámetros de la búsqueda que queremos realizar. Desde el Codex podéis ver todos los parámetros implementados , estos son solo los tipos posibles de parámetros que posee esta fantástica API

\[box\]

- [5.1 Author Parameters]("#)
- [5.2 Category Parameters]("#)
- [5.3 Tag Parameters]("#)
- [5.4 Taxonomy Parameters]("#)
- [5.5 Search Parameter]("#)
- [5.6 Post & Page Parameters]("#)
- [5.7 Type Parameters]("#)
- [5.8 Status Parameters]("#)
- [5.9 Pagination Parameters]("#)
- [5.10 Order & Orderby Parameters]("#)
- [5.11 Time Parameters]("#)
- [5.12 Custom Field Parameters]("#)
- [5.13 Permission Parameters]("#)
- [5.14 Caching Parameters]("#)
- [5.15 Return Fields Parameter]("#)

\[/box\]

 

Siempre puedes usar la técnica antigua , generar una cadena  con la consulta  SQL

Para este caso se concatenan los parámetros separados por "&"

 

La mezcla en este caso no es una mejora.

Puedes tener que modificar un Loop realizado con arrays , puedes obtener la consulta final y concatenar parámetros. Esto es una _GUARRADA_ ,  si funciona pero crear un array para la búsqueda y poder entender el código después no tienen precio.

En mi caso trabajo , siempre que puedo , con temas hijos , así que regenero la plantilla casi por completo. Coges el código antiguo y lo modificas siguiendo las reglas de estilos de WordPress.

### Recursos:

He buscado un poco por internet para realizar esta tarea  y he encontrado una persona con más experiencia que yo  , explicando perfectamente los tipos de código que nos podemos encontrar en los Loop.

Post: [Editando el "loop" de WordPress](https://hbravo.com/editar-loop-wordpres/ "Editando el “loop” de WordPress")

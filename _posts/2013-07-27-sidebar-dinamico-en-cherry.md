---
layout: single
title: "Sidebar dinámico en Cherry"
date: "2013-07-27"
categories: dev
---

# sidebar dinámica en Cherry

\[flickr\]https://www.flickr.com/photos/12949201@N08/9348328122/\[/flickr\]

Estoy trabajando con el Framwork de Cherry y me he encontrado un sidebar estático , un poco malo. No es normal que te dejen editarlo con toda la felicidad del mundo en el backer de WP y luego resulta que no se ve ni un widget que no hayas metido a código en sidebar.php.

## Localizar el fichero

Tener en cuenta que aunque uses un tema que use el Framwork debes de mirar quien genera el sidebar , el tema hijo o el de Cherry. Para verificarlo tenemos que revisar el código del functions.php del tema hijo y buscas la función de registro de sidebar .

 
register\_sidebar(array(

Si no lo tenemos ahí  el siguiente fichero a revisar es el del framework  , para encontrarlo es muy divertido ya que utiliza un _include_ del fichero _sidebar-init.php_

 
include\_once (CHILD\_DIR . '/includes/sidebar-init.php');

Con esto hemos de revisar el fichero sidebar-init.php en la carpeta _includes_ del FW Cherry

Aquí vemos que en los comentarios indican que es estática , así que hemos de hacer un nuevo script , en este fichero , para tener en el mismo lugar la nueva.

## Mi script

Esto es todo el código que me ha hecho falta  , se ha guardado en el fichero sidebar.php de la carpeta del Framework Cherry 2.0

 

## Notas

\[box type="info"\] Nota: He utilizado el campo id utilizado en el registro del sidebar en el fichero functions. \[/box\]

Con esto y un bizcocho hemos mejorado un Framework, ahora administrarlo va a ser un atarea más simple. No en vano hemos perdido la actualización del Framework Cherry de forma automática tendremos que manejar este fichero modificado para utilizar en la siguiente actualización

## Fuentes:

[Wordpress: Un sidebar diferente en cada-pagina](https://isanbi.wordpress.com/2010/11/16/wordpress-sidebar-diferente-en-cada-pagina/ "wordpress-sidebar-diferente-en-cada-pagina")

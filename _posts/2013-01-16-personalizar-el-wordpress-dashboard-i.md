---
layout: posts
title: "Personalizar el wordpress dashboard I"
date: "2013-01-16"
categories: dev
---

Hoy toca eliminar todo los elementos del wordpress dashboard . Queremos que sea simple y sencillo para los futuros usuarios . El planteamiento es sencillo , si no hay opciones para distraerse mejor que mejor. Como entorno de pruebas voy a utilizar un espacio **MultiSite** de WordPress.  Permitiré al rol Administrador poder ver el escritorio completo  , para ello utilizaré la función  _"is\_super\_admin()"_

_**Estas modificaciones se realizan el plugin de funciones o en functions.php**_

Vamos a mejorar la funcionalidad del wordpress dashboard

El escritorio se divide en tres apartados:

- Mensaje de HOLA , le tengo un poco de manía
- Menús de administración
- Opciones de pantalla
- Pestaña de ayuda
- Widgets de escritorio
- CSS diferente para el escritorio

Las acciones requeridas para personalizar estos puntos pasan por utilizar el fichero _functions.php_ y diferentes filtro y acciones , incluso utilizaremos algún _truquillo_ de CSS para ocultar elementos. Empezando por el principio

   //Eliminar el mensaje de Bienvenida de WP
   add\_action( 'load-index.php', 'aw\_hide\_welcome\_panel\_for\_multisite' );
   function aw\_hide\_welcome\_panel\_for\_multisite() {
           if ( ! is\_multisite() ) // si quieres usar este código en un WordPress sencillo borra esta línea
                   return;
           if ( 2 === (int) get\_user\_meta( get\_current\_user\_id(), 'show\_welcome\_panel', TRUE ) )
                   update\_user\_meta( get\_current\_user\_id(), 'show\_welcome\_panel', 0 );
   }

  //Ocultar menús de administracion
  if ( !is\_super\_admin() ) {
          add\_action( 'admin\_init', 'quitar\_menus' );
  }
  function quitar\_menus() {
  remove\_menu\_page('edit.php'); //Entradas
  remove\_menu\_page('edit.php?post\_type=acf'); //Advance custom field
  remove\_menu\_page('options-general.php'); //Ajustes
  remove\_menu\_page('tools.php'); //Herramientas
  remove\_menu\_page('themes.php'); //Apariencia
  remove\_menu\_page('edit.php?post\_type=page'); //Paginas
  remove\_menu\_page('edit-comments.php'); //Comentarios
  }

  //Ocultar la pestania de "Opciones de pantalla" en el escritorio
  if ( !is\_super\_admin() ) {
          add\_filter('screen\_options\_show\_screen', 'eliminar\_opciones\_pantalla');
  }
  function eliminar\_opciones\_pantalla(){
  return false;
  }

//Ocultar la pestania de ayuda en el escritorio
  if ( !is\_super\_admin() ) {
          add\_action('admin\_head', 'hide\_help');
  }
  function hide\_help() {
      echo '

';

//Ocultar widgets del escritorio
  if ( !is\_super\_admin() ) {
          add\_action('wp\_dashboard\_setup', 'quitar\_widgets\_escritorio' );
  }
  function quitar\_widgets\_escritorio() {
          global $wp\_meta\_boxes;
unset($wp\_meta\_boxes\['dashboard'\]\['side'\]\['core'\]\['dashboard\_quick\_press'\]);
unset($wp\_meta\_boxes\['dashboard'\]\['normal'\]\['core'\]\['dashboard\_incoming\_links'\]);
unset($wp\_meta\_boxes\['dashboard'\]\['normal'\]\['core'\]\['dashboard\_right\_now'\]);
unset($wp\_meta\_boxes\['dashboard'\]\['normal'\]\['core'\]\['dashboard\_plugins'\]);
unset($wp\_meta\_boxes\['dashboard'\]\['normal'\]\['core'\]\['dashboard\_recent\_drafts'\]);
unset($wp\_meta\_boxes\['dashboard'\]\['normal'\]\['core'\]\['dashboard\_recent\_comments'\]);
unset($wp\_meta\_boxes\['dashboard'\]\['side'\]\['core'\]\['dashboard\_primary'\]);
unset($wp\_meta\_boxes\['dashboard'\]\['side'\]\['core'\]\['dashboard\_secondary'\]);
}

**Con esto y un bizcocho tenemos un poco más personalizado nuestro wordpress dashboard**

Fuente : [Quitar widgets por defecto en el escritorio](https://ayudawordpress.com/quitar-widgets-por-defecto-en-el-escritorio/ "quitar-widgets-por-defecto-en-el-escritorio") [Quitar la pestana de ayuda en la administracion de wordpress](https://noticiaswordpress.com/2011/11/25/quitar-la-pestana-de-ayuda-en-la-administracion-de-wordpress/ "quitar-la-pestana-de-ayuda-en-la-administracion-de-wordpress") [como eliminar la pestaña opciones-de pantalla en wordpress](https://www.aquihaydominios.com/blog/como-eliminar-la-pestana-opciones-de-pantalla-en-wordpress/ "como-eliminar-la-pestana-opciones-de-pantalla-en-wordpress")

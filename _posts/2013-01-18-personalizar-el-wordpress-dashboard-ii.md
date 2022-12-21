---
layout: post
title: "Personalizar el wordpress dashboard II"
date: "2013-01-18"
categories: dev
---

Seguimos con las personalizaciones del wordpress dashboard. En este caso generaremos un plugin con diferentes hacks  que modificarán el aspecto , intentamos mejorar la adaptación de la herramienta a nuestros propósitos.

Estas son las modificaciones que presentaremos para nuestro wordpress dashboard

- Modificar el pie izquierdo
- Modificar el pie derecho
- Aplicar un CSS

//Modificar el pie izquierdo

add\_filter('admin\_footer\_text', 'left\_admin\_footer\_text\_output'); //left side
function left\_admin\_footer\_text\_output($text) {
    $text = 'Luis Puente';
    return $text;
}

//Modificar el pie derecho
add\_filter('update\_footer', 'right\_admin\_footer\_text\_output', 11); //right side
function right\_admin\_footer\_text\_output($text) {
    $text = 'MiWardrobe.com';
    return $text;
}

 //Incluir mi propio CSS
function my\_admin\_head() {
        echo '				';
}
add\_action('admin\_head', 'my\_admin\_head');

Se debe señalar que el nuevo fichero CSS debe de estar en la carpeta del plugin

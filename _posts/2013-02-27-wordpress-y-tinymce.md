---
layout: posts
title: "TinyMCE y WordPress"
date: "2013-02-27"
categories: dev
---

Es el edito WYSIWYG por defecto de WordPress. Este softare es un JS integrado en el CMS , así que si queremos modificar algo en lo más limpio será preguntar a la API de WordPress a ver que nos cuenta.

WordPress y TinyMCE

Buscamos un Hook para lanzar nuestra modificación , será en la inicialización del "Editor"

La referencia encontrada es  'tiny\_mce\_before\_init' y utilizaremos un filtro

add\_filter('tiny\_mce\_before\_init', 'fb\_change\_mce\_buttons');

Ahora necesitamos buscar la forma en la que se pasan los parámetros al TinyMCE. en la Web del proyecto tenemos  un [Wiki](https://www.tinymce.com/wiki.php/Configuration "Wiki configuración TinyMCE") donde podemos encontrar todas las variables de invocación.

Llegado a este punto tenemos el cuando  y el que debemos de trasmitir al editor para personalizar. Nos falta el como y ahí es donde entra WordPress , nos proporciona acceso libre a todas las configuraciones utilizando diferentes arrays extraídos de  la documentación de  TinyMCE

$initArray\['theme\_advanced\_blockformats'\] = 'p,address,pre,code,h3,h4,h5,h6';
$initArray\['theme\_advanced\_disable'\] = 'forecolor';

Con esto debemos crear una función invocada desde el filtro indicado y con las variables que deseamos configurar en el el editor. Yo he optado por eliminar todos los botones

$initArray\['theme\_advanced\_disable'\] = '"bold,italic,underline,strikethrough,justifyleft,justifycenter,justifyright,justifyfull,bullist,numlist,outdent,indent,cut,copy,paste,undo,redo,link,unlink,image,cleanup,help,code,hr,removeformat,formatselect,fontselect,fontsizeselect,styleselect,sub,sup,forecolor,backcolor,forecolorpicker,backcolorpicker,charmap,visualaid,anchor,newdocument,blockquote,separato"';

La función quedaría de esta forma

function disable\_tinymce\_buttons( $initArray ) {
		$initArray\['theme\_advanced\_disable'\] = '"bold,italic,underline,strikethrough,justifyleft,justifycenter,justifyright,justifyfull,bullist,numlist,outdent,indent,cut,copy,paste,undo,redo,link,unlink,image,cleanup,help,code,hr,removeformat,formatselect,fontselect,fontsizeselect,styleselect,sub,sup,forecolor,backcolor,forecolorpicker,backcolorpicker,charmap,visualaid,anchor,newdocument,blockquote,separato"';
		return $initArray;
		}

			add\_filter('tiny\_mce\_before\_init', 'disable\_tinymce\_buttons');

fuentes: [Personalizar TinyMCE en WordPress](https://wpengineer.com/1963/customize-wordpress-wysiwyg-editor/ "Personalizar TinyMCE en WordPress") [Parametros de configuraciónde TinyMCE](https://www.tinymce.com/wiki.php/Configuration "Parametros de configuraciónde TinyMCE") [Deshabilitar botones en TinyMCE](https://www.tinymce.com/wiki.php/Configuration:theme_advanced_disable "Deshabilitar botones en TinyMCE") [Listado de botones de TinyMCE](https://www.tinymce.com/wiki.php/Buttons/controls "Listado de botones de TinyMCE")

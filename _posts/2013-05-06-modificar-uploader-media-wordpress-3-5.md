---
layout: posts
title: "Modificar pestañas de Uploader Media WordPress +3.5"
date: "2013-05-06"
categories: dev
---

# Uploader Media WordPress

En el paso a 3.5 se modifico el Uploader Media WordPress , esto incluyó principalmente el "drag and drop" y el uso de un popup integrado muy bonito. Por el camino se ha perdido la capacidad de varios hooks para modificar la antigua ventana.

El como modificar estas ventanas se divide en dos partes , las pestañas y los atributos. La modificación también se puede atacar desde varios frentes , JavaScript (JQuery , Backbone) y hooks.

Nota:No me gusta eliminar elementos ni trabajar con la interfaz de JS si no esta totalmente claro que ha de ejecutarse en cliente , prefiero enviar siempre el código HTML perfectamente maquetado.

Espero que pronto tengamos unos hooks para trabajar con el Uploader Media WordPress. El primer paso esta dado y para pestañas ya tenemos algo.

El JavaScript lo encontraras en internet de formas muy parecidas , ya que es un "workaround"/parche fácil de implementar. Para este caso utilizaremos el fichero de funciones del tema y así evitaremos tener que modificar diferente PHP y poder estropear el maquetado. en la siguiente entrega veremos como trabajar con JS y el Uploader Media WordPress

Eliminar las pestañas

- Inserta de URL
- Crear Galería

Para este paso utilizaremos un hook de WordPress y un array de campos que deshabilitaremos dos opciones.

hook: media\_view\_strings

//Elimina las opciones de insertar imágenes desde URL y crear galería

		function remove\_media\_tab($strings) {

			unset(
				$strings\["insertFromUrlTitle"\],
				$strings\['createGalleryTitle'\]
			);
			return $strings;
		}
		add\_filter('media\_view\_strings','remove\_media\_tab');

Buscando las cadenas di con este [increible post](https://sumtips.com/2012/12/add-remove-tab-wordpress-3-5-media-upload-page.html "Add or Remove Tabs from WordPress 3.5 Media Manager") sobre modificación de pestañas en el Uploader Media Wordpress , siempre pensado en versiones 3.5+. Siguiendo el filtro por los ficheros del core he localizado estas opciones modificables

$strings\['selected'\],  //Removes Upload Files & Media Library links in Insert Media tab
$strings\['insertMediaTitle'\],  //Insert Media
$strings\['uploadFilesTitle'\],  //Upload Files
$strings\['mediaLibraryTitle'\],  //Media Library
$strings\['createGalleryTitle'\],  //Create Gallery
$strings\['setFeaturedImageTitle'\],  //Set Featured Image
$strings\['insertFromUrlTitle'\]  //Insert from URL

Es función la situaremos en el fichero functions.php de nuestro tema activo. Utilizaremos el mismo filtro

## Fuentes:

[WP 3.5 and Hiding Media Tabs](https://wordpress.org/support/topic/wp-35-and-media-tabs "WP 3.5 and Hiding Media Tabs")

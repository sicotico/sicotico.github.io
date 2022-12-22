---
layout: posts
title: "WP 2.8 + Flickr + Lightbox 2"
date: "2009-06-30"
categories: dev
---

Me he pasado una tarde buscando plugins para integrar WordPress 2.8 y Flickr .

He probado:

- Flicker Gallery:  Es un poc incomodo tener que utilizar shortcodes , yo prefiero dejarlo todo automatizado
- Fllickr Manager : Falla a la hora de insertar la imagen que se bloquea y no hace nada
- Flicker Phot0 Album:  Funciona perfecto

Al principio no aparece la opción del visor que quiero utilizar , pero rebuscando un poco hay unas instrucciones para activarlo siempre . Se modifica el fichero wp-config.php.

Activar Lightbox u otro modo compatible

Desde el tablero vamos a Opciones--> Photo Album

En la sección

Personalizaciones

**Popup Overlays:** Add Lightbox style popup overlays to displays to your photos. Demo \- Instrucciones

Aquí tenemos las lineas que debemos escribir para activar uno u otro visor

A parte tenemos que añadir el plugin Lightbox 2 y activarlo.

[![hp-w2216jpg](images/3569990224_1347447dcf_t.jpg)](https://farm3.static.flickr.com/2450/3569990224_1347447dcf.jpg "hp-w2216jpg")

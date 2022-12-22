---
layout: posts
title: "DHTML y CSS"
date: "2009-05-07"
categories: dev
---

Después de todas esas charlas de Alex , sobre semántica y mas cosas raras , me ha tocado currar un poco en el campo web y le he hecho caso. Lo primero fue encuadrar todo el contenido en capas , alguna tabla si que tengo pero para un formulario me es más fácil. Cada una tiene un ID asignado para referirnos a ella.

Ahora empezamos con el CSS , yo tengo costumbre de editar las propiedades de "h1....h5" para poner todos los títulos iguales. Después añado los relacionados con "a:"

h1, h2 {
    text-align: left;
    letter-spacing: 6px;
    font-size: 1.4em;
    color: #be7429;
    font-weight: normal;
    width: 450px;
}

a:link {
   color: #be7429;
   font-weight: normal;
   text-decoration: none;
}

a:link:hover {
   color: #be7429;
   font-weight: normal;
   text-decoration: underline;
}

Lo básico ya esta hecho , ahora los ID de las capas no facilitaran el acceso a sus propiedades . Para referirnos a un elemento de HTML usamos el #ID {}. Con esto podemos dar todas las personalizaciones que queramos sin destrozar el código HTML.

Fichero html

Fichero CSS #aniadir\_ins { margin: 0 auto 0 auto; }

De paso aprovecho que así deje centrada la capa respecto de la ventana

Algo de JS debe de haber así que he puesto un boton que vuelve siempre a la pagina principal :

Inicio

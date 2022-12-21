---
layout: post
title: "Barra de Navegación"
date: "2010-01-04"
categories: dev
---

Con la renovación del web he tenido que aplicarme un poco en esto del css , semántica y no mezclar estructura con no se que.

Este es el código que he utilizado para crear una barra de navegación horizontal basada en una lista `ul` de HTML. Remarcamos lo importante: `display: inline` --> propiedad aplicada a los elementos de la lista , les organiza de forma horizontal El elemento `#barra` depende directamente del DOM HTML por eso tiene posición `relative`

#barra ul {
margin: 0;
padding: 0;
list-style-type: none;
list-style-image: none;
text-decoration: none ;
}
#barra li {
display: inline;
background: white;
margin: 0.5em;
padding: 0.3em;
width: 200px;
border: 0.2em solid black }
#barra{
position: relative;
border: 5px solid black;
left: 50px;
width: 660px;
height: 20px;
}

                       

                               
                               

                                       - [Blog](wp/)
                                           
- [JS Google Maps](jsgooglemaps/)
                                           
- [Calculador de rutas](rutas/)
                                           
- [Buscador](buscador/)
                                           
- [Autor](#)
                                           
- [Inicio](/)

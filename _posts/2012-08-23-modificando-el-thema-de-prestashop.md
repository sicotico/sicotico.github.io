---
layout: post
title: "Modificando el thema de Prestashop"
date: "2012-08-23"
categories: dev
---

Vamos a tomar notas de las modificaciones que estoy haciendo en el grobal.ccs de prestashop.

Este fichero se encuentra en:

./themes/"nombre del tema"/css/

Primero el fichero global.css tiene carácter general  , pero adicionalmente existe otros css en niveles inferiores específicos para los diferentes bloques que posee el CMS. estos se encuentran en:

./themes/"nombre del tema"/css/modules

Ahora entrando en faena , quiero dejar un registro a modo de nota de las modificaciones que voy haciendo en este fichero y en los que sea necesario:

 220 img.logo {
 221         float: left;
 222         margin-top: 0.5em;
 223         margin-bottom: 0.5em;
 224         font-size: 2em;
 225         font-weight: bold

Ahí retoco el espacio inferiro del logo , ya que no deja ningun espacio y a mi me gusta con algo de fondo.Para ello utilizo **_margin-bottom: 0.5em_**

798         div.block .block\_content {
799         border-left: 1px #d0d3d8;
800         border-right: 1px #d0d3d8;
801         padding: 0 0.7em;
802         /\*background: #f1f2f4 url('../img/block\_bg.jpg') repeat-x bottom left;\*/
803         background: rgb(237,76,76);
804         min-height: 16px
805 }

Elimino la imagen del fondo y cargamos un color directamente.

  15 body {
  16         /\*background-color: white;\*/
  17         background-color: black ;
  18         font-size: 11px;
  19         font-family: Verdana, Arial, Helvetica, Sans-Serif;
  20         color: #5d717e;
  21         text-align: center
  22 }

Cambiamos el color de fondo

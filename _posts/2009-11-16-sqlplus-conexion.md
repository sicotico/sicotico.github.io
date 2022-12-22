---
layout: posts
title: "Sqlplus conexion"
date: "2009-11-16"
categories: software
---

Hoy ha sido el día ,  mi primera vez a pelo con Oracle

Tras una conexión en ssh ,  y ahora que cojones hago con esto. Necesito un par de campos de una tabla y nos e como sacarlos:

Conexión:

`sqlplus user/pass@SID`

Ver la vistas disponibles:

`select * from tab;`

Información de la tabla o vista;

`desc <nombre de la tabla o vista>;`

Mi primera consulta:

`select <campo[1],campo[2],..> from <tabla``[1]``,tabla``[2]``,..> where tabla[n].campo[n] like '%cadena%'`

Acordarse comillas simples para literales y % como si fuera asterisco

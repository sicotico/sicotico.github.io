---
layout: posts
title: "Buscar elementos duplicados en oracle"
date: "2009-11-19"
categories: software
---

Muestra una lista de elemento con dos columnas , el numero de veces repetidas y el campos identificador

`select count(*),<campo1> from <tabla> group by <campo1> having count(*) > 1;`

Para mostrar solo los elenentos repetidos

`select <campo1> from <tabla> group by <campo1> having count(*) > 1;`

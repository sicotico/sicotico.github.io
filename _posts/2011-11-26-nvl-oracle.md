---
layout: post
title: "NVL Oracle"
date: "2011-11-26"
categories: software
---

# Sintaxis.bases\_datos\_ora\_11g

NVL(expr1,expr2)

# Proposito.

La función NVL() te permite sustituir valores null con una cadena en los resultados de una consulta. Si expr1 es nulo, NVL devuelve expr2. Si expr1 no es nulo, NVL devuelve expr1.

Los argumentos expr1 y expr2 pueden tener cualquier tipo de dato. Si sus tipos de datos son diferentes, entonces la base de datos Oracle convierte implícitamente al otro. Si no se puede convertir de forma implícita, la base de datos devuelve un error. La conversión implícita se lleva a cabo de la siguiente manera:

Si expr1 es de tipo carácter, la base de datos Oracle convierte expr2 al tipo de datos de expr1 antes de compararlos y devuelve un VARCHAR2 en el juego de caracteres de expr1

Si expr1 es de tipo numérico, base de datos Oracle determina qué argumento tiene la máxima prioridad numérica, convierte implícitamente el argumento válido para ese tipo de datos, y devuelve ese tipo de datos

La función NVL() se puede utilizar tanto en Oracle 10g como en Oracle 11g.

# Ejemplos

En este ejemplo aparece un listado de productos con su descuento, si descuento es null colocamos un 0.

1.SELECT Descripcion, NVL(TO\_CHAR(descuento), 0) Descuento
2. FROM productos
3. WHERE precio < 12
4. ORDER BY 1;

DESCRIPCION DESCUENTO
--------------------------- --------------
Cuaderno anillas 10 A4 0
Grapadora pequeña 10
Paquete 500 folios A4 0
Portaminas 0.5 2
Rotulador rojo 4

En este otro ejemplo si descuento es null colocamos una cadena de caracteres ‘Sin Descuento’.

1.SELECT Descripcion, NVL(TO\_CHAR(descuento), 'Sin Descuento') Descuento
2. FROM productos
3. WHERE precio < 12
4. ORDER BY 1;

DESCRIPCION DESCUENTO
----------------------- ---------------
Cuaderno anillas 10 A4 Sin Descuento
Grapadora pequeña 10
Paquete 500 folios A4 Sin Descuento
Portaminas 0.5 2
Rotulador rojo 4

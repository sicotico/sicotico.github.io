---
layout: posts
title: "Operador UNION"
date: "2011-09-06"
categories: viajes
---

Vaya descubrimiento , se nota que soy nuevo en esta lindes.

La situación es la siguiente no soy capaz de articular con operadores lógicos (AND , OR , NOT)

SELECT
   COUNT(campo1) "Numero", r.campo3 "Nombre "
FROM
    schema1.Tabla1 t, schema1.Tabla2 r
WHERE
    t.campo1 = r.campo1 AND t.campo2 IN (1,2,3,4)
GROUP BY r.campo1

UNION ALL

SELECT
    COUNT(campo1) "Numero", 'Texto AUX' "Nombre"
FROM
    schema1.Tabla1 S t, schema1.Tabla2 r
WHERE
    t.campo1 = r.campo1 AND t.campo3 IS NOT NULL

Utilizando "UNION" se han de generar las dos consultas con el mismo numero de columnas. El incrementar las columnas con la función "COUNT" , implica utilizar un "GROUP BY" si necesitamos que aparezcan más campos. La solución para este caso fue inventarte un campo y así tener un funcionamiento correcto del "UNION" y además no es susceptible de "COUNT" por lo que no hace falta usar "GROUP BY".

Tenemos una consulta perfecta.

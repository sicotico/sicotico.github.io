---
layout: post
title: "Consulta de campos fecha en Oracle"
date: "2010-05-20"
categories: software
---

Cuando consultamos un dato fecha con:

SELECT "CAMPO"  FROM "TABLA" WHERE

Nos devuelve solo el año , si un DBA ha pasador ahí , el puede cambiar el formato por defecto de salida de DATE

SELECT "CAMPO1",TO\_CHAR("CAMPO2",'ddmmyyyy hh24:mi:ss')
FROM "TABLA" WHERE

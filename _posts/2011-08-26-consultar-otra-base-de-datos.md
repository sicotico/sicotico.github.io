---
layout: posts
title: "Consultar otra base de datos"
date: "2011-08-26"
categories: dev
---

Si tenemos un Servidor de SQL Server y varias bases de datos dentro , este post tiene sentido.

Hay veces que se da este caso , nos encontramos en una base de datos y necesitamos acceder a tablas de otra diferente. Como ya indicamos, debe de ser el mismo servidor.

La sintaxis de la consulta es:

\[nombre de DB\].\[objeto\].tabla

¡Atentos a poner los corchetes , ya que son obligatorios!

Ejemplo:

\[ServerDB\].\[dbo\].tabla1

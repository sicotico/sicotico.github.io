---

title: "SQL Server error 4064"
date: "2009-11-19"
categories: 
  - "sin-categoria"
---

Mensaje de error: `No se puede abrir la base de datos de usuario predeterminada`

La solucion:

`sp_defaultdb [ @loginame= ] 'login', [ @defdb= ] 'database'`

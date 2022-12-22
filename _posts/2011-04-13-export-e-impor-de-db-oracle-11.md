---
layout: posts
title: "export e impor de DB Oracle 11"
date: "2011-04-13"
categories: software
---

### Para hacer un export

`expdp user/pass@INSTANCIA directory="DIR" dumpfile=fichero.dmp logfile=fichero.log`

Poniendo el nombre del fichero dmp y log que quieras (si es identificativo mejor)  

### Para hacer un export

  
Borrar las tablas del esquema de la "INSTANCIA" de PRE antes de realizar el import.

`impdp user/pass@INSTANCIA directory="DIR" dumpfile=fichero.dmp logfile=fichero.log`

poniendo el nombre del fichero dmp que hemos copiado y el nombre del log que quieras

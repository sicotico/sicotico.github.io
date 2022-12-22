---
layout: posts
title: "PowerShell y comandos del sistema"
date: "2012-07-16"
categories: dev windows
---

Siempre sabemos que comandos ejecutamos para realizar muchas tareas  y a la hora de crear el VBScript  nos quedábamos en blanco con el dichoso objeto que debíamos utilizar. Hacer un par de scripts al año no te da soltura. En mi primer problema técnico con este lenguaje me he encontrado muchas soluciones basadas en el concepto de ejecutar comando de cmd , dentro del script . Para esto se recurre a un recubrimiento del lenguaje , en VBS era crear un proceso y dentro de el ejecutábamos lo que queríamos , a nivel de sistema operativo quedaba registrado como un procesos de w/cscript.

 

C:UsersAdministrator>type foo.ps1
Invoke-Expression -Command "dir e:temp"

PS E:temp> Invoke-Expression -Command "dir h:temp"

    Directory: H:temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        30/07/2011      6:28            fffff
d----        11/05/2011     20:27            f\_gggg
-a---        02/05/2011     20:60        281 hola.ps1
-a---        14/06/2011     23:10       6240 ffffffffff.jar
-a---        10/06/2011      6:38       2900 rrr\_444.rar

Tenemos un herramienta fantastica para salir del paso en momentos críticos

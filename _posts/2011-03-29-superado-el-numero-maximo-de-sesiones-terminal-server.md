---
layout: posts
title: "Superado el numero máximo de sesiones terminal server"
date: "2011-03-29"
categories: windows
---

Odio este error:

_**terminal server has exceeded the maximum number of allowed connections**_

Conectamos con el servidor

`net use /user:[username] \servernameshare`

Preguntamos por la sesiones abiertas

`query session /server:servername`

Eliminamos una sesin

`reset session [ID] /server:servername`

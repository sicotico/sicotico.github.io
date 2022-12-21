---
layout: post
title: "Autenticar recurso en windows"
date: "2010-05-26"
categories: windows
---

Esto habilita el acceso a un recurso con clave , durante la sesión.

     net use o: \\servidorcarpeta pass /user:login
     copy \\servidorcarpetafichero c:

Ahora tenemos iniciada una sesión en ese recurso compartido y podemos interactuar con el cómodamente. Esto se puede utilizar en bat ejecutado en logon

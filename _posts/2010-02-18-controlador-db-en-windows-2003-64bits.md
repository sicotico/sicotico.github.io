---
layout: single
title: "Controlador DB en Windows 2003 64bits"
date: "2010-02-18"
categories: windows
---

Esto es un problema cotidiano , por lo menos para mi. Tengo que crear un ODBC a un fichero Acces y resulta que no hay drivers instalados.

[![](images/ODBC_64-300x247.jpg "ODBC 64bits")](https://luispuente.net/wp-content/uploads/2010/02/ODBC_64.jpg)

Yo con mi buena intención me busco el MDAC para instalarme lo. Sin ningún  resultado.  Tras comentarlo aun compañero  , un poco tocado y con tablas , encontró la existencia de dos panales ODBC , uno para drivers de 64 y otro para los de 32. Por defecto te aparece el de 64 y claro si te instalar un SQL Server para 64 pues el driver lo tienes.

Este es el ejecutables del panel ODBC para 32

C:WINDOWSSysWOW64odbcad32.exe

[![](images/ODBC_32-300x247.jpg "ODBC 32")](https://luispuente.net/wp-content/uploads/2010/02/ODBC_32.jpg)

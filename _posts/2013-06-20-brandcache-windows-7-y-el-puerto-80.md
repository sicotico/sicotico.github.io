---
layout: posts
title: "BrandCache Windows 7  y el puerto 80"
date: "2013-06-20"
categories: windows
---

## BrandCache

Este post  aparece por las pocas veces que utilizo Windows para el trabajo web. Son mas familiares los entornos derivados de debian.  No puedo dejar de apuntar como gestiona Windows 7 este puerto para futuros casos en los que me haya olvidado completamente como lo he solucionado.

Tengo un Windows 7 instalado y me dispongo a utilizar Xampp Lite , la instalación por defecto con todo el pack Apache+PHP+MySQL+PHPMyAdmin . Al iniciar el servicio de Apache solo hace que fallar y el paso inicial es revisar si el puerto 80 esta ocupado. Así es  esta ocupado por el propio sistema operativo.

\[flickr\]https://secure.flickr.com/photos/12949201@N08/9047402715/\[/flickr\]

Las dos vías posibles para abordar el problema  son:

Los servicio de  SQLServer , que aun des instalado puede haber dejado una entrada el registro solicitando a svchost que escuche en ese puerto.

_El SQL Server no era mi caso ya que indicaba e como propietario el usuario SYSTEM_

La suerte estaba de mi lado  y el problema era del sistema operativo , esto es verificable con la herramienta de control de puerto de Xampp , en ella se indica que SYSTEM esta usando el puerto 80 y no svchost

Tenemos un windows que ocupa el puerto 80 , hay que buscar que servicio se les ha ocurrido colocar en este puerto.

La respuesta es  :

_**BrandCache**_

Ahora ya sabes con quien nos jugamos los cuartos.  Esta es la única [referencia](https://technet.microsoft.com/en-us/network/dd425028.aspx "BrandCache") de BrandCache que he encontrado sobre el .

Vamos a los servicios de windows a deshabilitarlo

Fuente: [Microbiablog.com](https://www.microbiablog.com/herramientas/problema-apache-xampp-con-puerto-80-en-windows-7/ "Apache Xampp con puerto 80 en Windows-7")

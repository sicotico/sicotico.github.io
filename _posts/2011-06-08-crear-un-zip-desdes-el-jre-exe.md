---
layout: post
title: "Crear un zip desdes el JRE.exe"
date: "2011-06-08"
categories: dev
---

No fui capaz de obtenerlo de la web  , para la plataforma Windows x64 , así que con el ejecutable jre-1\_5\_0\_22-windows-amd64.exe , [Universal Extractor](https://www.legroom.net/software/uniextract "Universal Extractor") y msiexec me he creado mi propio zip.

La base para currar tanto para una estupidez como esta , es para tener dos jre corriendo en el mismo servidor windows. Esto en linux es bastante normal y sencillo , en Windows la dificulta es conseguir el paquete portable de java.

Con el ejecutable descargado utilizamos el Universal Extractor y te ofrece tres opciones de extracción, para la versión de 64 utilice "isxunpack extacción". Genero una carpeta con un MSI. Utilizando las herramientas estándar de esta mapaquetizaciónquetación , "msiexec" puedes descomprimirlo fácilmente .

_msiexec /a RutaAlMSI /qb TARGETDIR=DirectorioExtraer_

_Al final me quede solo con la carpeta jre1.5\_22 que contiene las típicas carpetas bin , etc ...._

_La casualidad hizo que para la versión de 32 bits no fuera compatible el Universal Extractor y utilice simplemente el IZarc , primero descomprimiendo el exe y después cada uno de los zip internos que se generaron._

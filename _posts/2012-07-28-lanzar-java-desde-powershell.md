---
layout: post
title: "Lanzar Java desde PowerShell"
date: "2012-07-28"
categories: dev
---

Este caso ha sido un dolor de cabeza   ,  ejecutando PowerShell en un servidor de aplicaciones  tienen muchos inconvenientes técnicos. Su pongo que tenga alguna ventaja  , no la he conocido ni utilizado.

Teniendo un script en PowerShell y queremos invocar una aplicación java existente  desde un entorno "limitado"

`cd` `h:ficheros` set-item -path Env:CLASSPATH -value h:ficheros $hola2 = Invoke-Expression -Command "java apalicacion parametros" $env:Path

 

**Desglosando por lineas** veremos un poco mejor su funcionamient.

- Lo primero que vemos es un típico posicionamiento  en el directorio donde se encuentran los scripts
- Establecemos un entorno para que nuestro servidor de aplicaciones sepa donde tiene las "cosas"
- Ya comentamos el Invoke-Expression
- No podemos olvidar restablecer el entorno porque sino tendremos muchos problemas para ejecutar otras sentencias.

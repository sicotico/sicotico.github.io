---
layout: posts
title: "PowerShell Uso de parametros"
date: "2012-07-30"
categories: dev
---

Tiene un función integrada para gestionar nuestros parámetros. Estable un control sobre su contenido y si no se ha pasado via para metros el solo te lo solicita.

Param(

\[Parameter(Mandatory=$true)\]
$user1 = $null,

\[Parameter(Mandatory=$true)\]
$pass1 = $null
) #end param

---
layout: single
title: "PowerShell, un lugar por donde empezar"
date: "2012-07-14"
categories: dev windows
---

Tras una búsqueda en Google sobre este invento he dado con este blog [Aprende informática conmigo](https://www.aprendeinformaticaconmigo.com/powershell "Aprende informática conmigo") , el primer paso esta dado y ha sido fácil siguiendo los puntos en orden.

Para los impacientes como yo que desean ejecutar un script en los primero 3 minutos  de lectura nos encontraremos con errores un poco peculiares.  Por defecto viene restringido el uso de scripts en PowerShell por medidas de seguridad , algo poco corriente en otros sistemas.

[![](images/error_policy_powershell.png "error_policy_powershell")](https://luispuente.net/wp-content/uploads/2012/07/error_policy_powershell.png)

 

Debemos habilitar la política _ExecutionPolicy_ , para ello podemos revisar su estado con

Get-ExecutionPolicy

y modificar lo con

Set-ExecutionPolicy (restricted | allsigned | remotesigned | unrestricted)

Intentemos leerlo todo antes de hacer tus primeros pinitos

[Manual](https://technet.microsoft.com/es-es/library/cc196356) básico del technet de MSDN

---
layout: post
title: "PowerShell renombrado de ficheros"
date: "2018-05-09"
categories: PowerShell 
---

Para la expresión regular use la aplicación web [txt2re](https://txt2re.com/index.php3?s=Fullmetal%20Alchemist%20Shinsetsu%20-%2030%20[10A879D9]&1)

Se aplico a este formato de nombre de fichero :

_Fullmetal Alchemist Shinsetsu - 30 \[10A879D9\]_

Pero es ampliable a varios subconjuntos de corchetes

_Fullmetal Alchemist Shinsetsu - 30 \[10A879D9\] \[hola\]_

La información para el comando la tienes en un caso de HowToGeek

Con esto eliminamos los corchetes de todos los ficheros , ya que realiza el for-each [automáticamente](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/rename-item?view=powershell-5.1).

_dir | rename-item -NewName {$\_.name -replace '\\\[.\*?\\\]',''}_

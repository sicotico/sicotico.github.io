---
layout: posts
title: "Cambiar rutas por defecto de Widnows"
date: "2008-06-05"
categories: windows
---

Alguna vez me toca limpiar ordenadores de amigos y claro son unos guarros instalando programas , se quedan sin espacio en c: . La solución , para que no te puteen la próxima vez , es modificar el registro de Windows cambiando las rutas del Escritorio , Mis Documentos .

Las instrucciones explican todas la rutas menos Archivos de Programas , la escusa es simple esta ruta es común a todos los usuarios así que estar en otra sección del registro.

Cambiar las rutas comunes (todas menos Archivos de programas)

HKEY\_CURRENT\_USERSoftwareMicrosoftWindowsCurrentVersionExplorerShell Folders

Cambiar la ruta Archivos de programas

HKEY\_LOCAL\_MACHINESOFTWAREMicrosoftWindowsCurrentVersion

La clave ProgramFilesDir

---
layout: single
title: "Manejo de ventanas en VBS"
date: "2008-01-23"
categories: dev
---

Mi codigo comentado:

`'miShell objeto que ejecuta el proceso 'miEjecución objeto asociado a la aplicación`

`Dim miShell, miEjecucion Set miShell = WScript.CreateObject("WScript.Shell")`

`On Error Resume Next`

' Wait for Uninstall ' -------------------------------------------------------------------------------- `Set miEjecucion = miShell.Exec("Ruta absoluta del ejecutable")`

`WScript.Sleep 500`

' -------------------------------------------------------------------------------- `cambioPantalla "Instalación"`

`miShell.SendKeys "{TAB}" ' <install> miShell.SendKeys "{ENTER}" ' <install>`

`WScript.Sleep 50`

' Espera a la correcta finalizacion de

`Do While miEjecucion.Status = 0 WScript.Sleep 500 Loop`

`cambioPantalla (miEjecucion.ProcessID)`

`miShell.SendKeys "{ENTER}" ' <Cerrar>`

' Salir del Script `WScript.Quit`

' Cambia la ventana activa por la del parametro o sale en 30 segundos ' dato puede ser Integer = Pid del proceso o String = Titulo de la ventana `SUB cambioPantalla( dato ) i = 0 DO bActive = miShell.AppActivate( dato ) WScript.Sleep 1000 i = i + 1 LOOP UNTIL bActive = TRUE OR i > 30 WScript.Sleep 100 END SUB`

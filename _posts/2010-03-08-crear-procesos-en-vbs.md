---
layout: post
title: "Crear procesos en VBS"
date: "2010-03-08"
categories: dev
---

Con esto creamos un objeto de sistema y le adjuntamos el ejecutable que deseemos. Así podemos tener cualquier proceso en background.

`Const HIDDEN_WINDOW = 12 strComputer = "." Set objWMIService = GetObject("winmgmts:" _ & "{impersonationLevel=impersonate}!\" & strComputer & "rootcimv2" ) Set objStartup = objWMIService.Get("Win32_ProcessStartup" ) Set objConfig = objStartup.SpawnInstance_ objConfig.ShowWindow = HIDDEN_WINDOW Set objProcess = GetObject("winmgmts:rootcimv2:Win32_Process" ) errReturn = objProcess.Create("Path completo con ejecutable y parámetros", "Path completo", objConfig, intProcessID)`

`If errReturn <> 0 Then Wscript.Echo "Process could not be created." & _ vbNewLine & "Command line: " & strCommand & _ vbNewLine & "Return value: " & intReturn Else Wscript.Echo "Process created." & _ vbNewLine & "Command line: " & strCommand & _ vbNewLine & "Process ID: " & intProcessID End If`

Fuente: [MSDN Win32\_Process](https://msdn.microsoft.com/en-us/library/aa389388%28VS.85%29.aspx)

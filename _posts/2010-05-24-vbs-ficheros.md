---
layout: post
title: "VBS Ficheros"
date: "2010-05-24"
categories: dev
---

**Manejo de ficheros** Codigo común para ficheros

Const ForReading = 1, ForWriting = 2, ForAppending = 8
Dim objfso
Dim objficherolog
Set objfso = CreateObject("Scripting.FileSystemObject")

**Existencia de fichero**

aux =  objfso.FileExists("C:Windowssystem32driversetchosts")

**Existencia de la unidad "c"**

aux = objfso.DriveExists("c")

**Existencia del directorio**

aux = objfso.FolderExists("C:Windows")

**Abrir Fichero**

Set objFicheroLog = objfso.OpenTextFile( "ruta completa y nombre del  log", ForAppending , True )

**Borrar Carpeta**

objfso.DeleteFolder "Ruta completa de la carpeta a borrar"

**Borrar Archivo**

objfso.DeleteFile "Ruta completa de la carpeta a borrar"

**Copiar fichero**

objfso.CopyFile "c:hola.txt","c:prueba"

**Comprobar si existe un fichero**

if not objfso.FileExists(strDirectorioProgramas &  "windowsnotepad.exe") then

**Insertar lineas o escribir en un fichero**

objTextFile.WriteLine("This line is written using WriteLine().")

objTextFile.Write ("This line is written using Write().")

objTextFile.WriteBlankLines(3)

**Leer un Fichero , una linea una posicion del Array**

Dim vector()
Do Until miFichero.AtEndOfStream
reDim Preserve vector(i)
vector(i) = mifichero.ReadLine
i = i + 1
Loop

**Leer un Fichero , de varias formas**

sReadLine = objTextFile.ReadLine

sRead = objTextFile.Read(4)

sReadAll = objTextFile.ReadAll

objTextFile.Close

---
layout: post
title: "Win-SSHFs Montar FS sobre SSH (Windows)"
date: "2013-08-03"
categories: win linux
---

## [Win-SSHFs](https://code.google.com/p/win-sshfs/ "win-sshfs")

Win-SSHFs  utiliza un sistema de ficheros linux en un windows a través de SSH. La arquitectura se basa en una conexión ssh a un servidor  en la que tengamos que trabajar con ficheros y un equipo windows como cliente.

Este sistema te permite montar el sistema de ficheros como una unidad de windows , además de la seguridad que otorga las conexiones ssh .

Personalmente el modificar ficheros y tener que subirlo al servidor me parece un atraso , el WinSCP o Filezilla se hacen izando una mezcla de un poco pesado ya que no fueron diseñados para esta tarea.

Utilizando:

- Dokan Library 0.6.0
- .NET
- Un poco de cabeza se ha creado este proyecto.

Sobre todo Win-SSHFs es fácil de usar

\[flickr\]https://www.flickr.com/photos/12949201@N08/9374177056/\[/flickr\]

Podemos asignar diferentes conexiones a letras del sistema y poder trabar de forma trasparente.

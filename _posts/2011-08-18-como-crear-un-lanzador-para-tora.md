---
layout: post
title: "Como crear un lanzador para TOra"
date: "2011-08-18"
categories: software
---

Depende de como instalemos TOra los launchers funcionan o no. Si instalamos del repo funcionaran. Si descargamos los sources y generamos un deb con soporte para oracle no funcionaran. Así que en ese caso crearemos un script "lanza\_tora.sh" para el arranque de la aplicacion TOra con:  
  
**xavi@xavi-VirtualBox:~$ vi lanza\_tora.sh**  
  

**#!/bin/bash  
export ORACLE\_BASE=/usr/lib/oracle/11.2  
export ORACLE\_HOME=$ORACLE\_BASE/client64  
export PATH=$PATH:$ORACLE\_HOME/bin  
export TNS\_ADMIN=/etc/oracle  
export LD\_LIBRARY\_PATH=$LD\_LIBRARY\_PATH:/usr/include/oracle/11.2/client64:****$ORACLE\_HOME****/lib  
/usr/bin/tora**

  
Las variables de entorno pueden variar dependiendo del cliente de oracle que instalamos y donde lo instalamos**.**  
  
Una vez generado el script editamos el fichero "tora.desktop" que hay en "/usr/share/applications" y modificamos la linea del Exec:  
  
**vi /usr/share/applications/tora.desktop**  
  
**Exec=/home/xavi/lanza\_tora.sh**  
  
Esto hará que el launcher del menú de aplicaciones funcione correctamente. Una vez llegados a este punto ya podemos crear el launcher en el escritorio que tomara por defecto los valores del fichero "tora.desktop" de "/usr/share/applications".

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-1511307601803860037?l=tablondesastre.blogspot.com)

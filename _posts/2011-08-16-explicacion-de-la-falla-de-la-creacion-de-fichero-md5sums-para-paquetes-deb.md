---
layout: post
title: "Explicación de la falla de la creación de fichero md5sums para paquetes deb"
date: "2011-08-16"
categories: linux
---

El siguiente comando nos permite crear el fichero md5sums con los hashes md5 de los ficheros que contiene el paquete deb.  
  
**find . -type f ! -regex '.\*.hg.\*' ! -regex '.\*?debian-binary.\*' ! -regex '.\*?DEBIAN.\*' -printf '%P ' | xargs md5sum > DEBIAN/md5sums**  
  
Vayamos por partes:  
  
**find . -type f**  
  
Esta parte del comando listara todos los ficheros, no directorios a partir de la ruta en que nos encontremos, recursivamente.  
  
**!**  
  
Operador de negacion, que debe ser seguido por una expresion.  
  
**\-regex '.\*.hg.\*'**  
  
Expresión regular, se puede interpretar como "ficheros que cumplen el patrón '$patrón'.  
  
**! -regex '.\*.hg.\*'**  
  
Se puede interpretar como "ficheros que no cumplen el patrón".   
  
**! -regex '.\*.hg.\*' ! -regex '.\*?debian-binary.\*' ! -regex '.\*?DEBIAN.\*'**  
  
Se puede interpretar como "ficheros que no cumplen el patrón '.\*.hg.\*', ni el patrón '.\*?debian-binary.\*', ni el patrón '.\*?DEBIAN.\*'  
  
**find . -type f ! -regex '.\*.hg.\*' ! -regex '.\*?debian-binary.\*' ! -regex '.\*?DEBIAN.\*'**  
  
Se puede interpretar como "busca los ficheros que no cumplen los patrones indicados por las expresiones en su path".  
  
**\-printf '%P '**  
  
Este argumento sirve para que la salida del comando find consista únicamente en el nombre del fichero y su ruta desde el punto en que nos encontramos sin el punto que indica la ruta en la que nos encontramos y separados por un espacio.  
  
**| xargs md5sum > DEBIAN/md5sums**  
  
Los ficheros encontrados por find que no cumplen los patrones indicados son pasados como argumentos al comando md5sum cuya salida genera el fichero md5sums en el directorio DEBIAN.  

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-3964113644876960417?l=tablondesastre.blogspot.com)

---
layout: single
title: "Copiar ficheros preservando los atributos"
date: "2011-08-20"
categories: linux
---

A veces por ejemplo queremos hacer replicas de puntos de montaje como el /usr para después desmontarlo y guarrear con el montando la copia temporalmente. Si decidimos realizar la replica copiando /usr hemos de tener en cuenta los atributos de los ficheros que contiene o mas tarde herramientas como sudo no funcionaran, por lo tanto:  
  
**sudo cp --preserve=all -R $origen $destino**

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-3103166191264552232?l=tablondesastre.blogspot.com)

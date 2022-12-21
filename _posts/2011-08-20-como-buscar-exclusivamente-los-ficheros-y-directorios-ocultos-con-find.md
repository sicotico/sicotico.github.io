---
layout: post
title: "Como buscar exclusivamente los ficheros y directorios ocultos con find"
date: "2011-08-20"
categories: linux
---

**find . -regex '.\*/..\*'**  
  
La expresión regular '.\*/..\*' se puede interpretar como:  
  
.\* - cualquier cadena de caracteres  
/  - barra  
. - punto  
.\* - cualquier cadena de caracteres

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-5125099170294857299?l=tablondesastre.blogspot.com)

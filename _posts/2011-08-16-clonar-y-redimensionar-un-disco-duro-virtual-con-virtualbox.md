---
layout: posts
title: "Clonar y redimensionar un disco duro virtual con virtualbox"
date: "2011-08-16"
categories: linux
---

Es importante tener en cuenta a la hora del redimensionado que el disco sea un disco dinámico y que solo puede expandirse. Además es necesario que no exista ningún snapshot de la maquina virtual, es caso de existir es necesario borrarlos antes del redimensionado.  
  
Clonacion:  
  
**VBoxManage clonehd $1.vdi $2.vdi**  
  
Redimensionado:  
  
**VBoxManage modifyhd $2.vdi --resize $tamaño\_en\_MB**

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-7423038765042317544?l=tablondesastre.blogspot.com)

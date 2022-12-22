---
layout: post
title: "Pantalla negra en VirtualBox"
date: "2007-11-06"
categories: vmware
---

Esto me ha ocurrido por despistado , al actualizar el VirtualBox a al version 1.5.2 borre todas las maquinas virtuales pero no los discos.Cree una nueva maquina virtual y le asigne un disco con un Windows 2003 Server y no me arrancaba, esta es la captura:

![Pantalla Negra en VirtualBox](images/virtualbox-negro.PNG)

Este problema viene de las caracteristicas de la CPU que seleccionamos al crear la primera maquina virtual.

![](images/Virtualbox-Opciones.PNG)

Si cuidamos bien el apartado de "Funcionalidades Extendidas" no ocurrira nada pero un sistema Windows no permite que se le cambien dichos parametros , no especifico cual es mejor o peor sino que hay que mantenerlo

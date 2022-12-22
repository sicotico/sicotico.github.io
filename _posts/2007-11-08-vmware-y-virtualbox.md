---
layout: post
title: "VMWare y VirtualBox"
date: "2007-11-08"
categories: vmware
---

Bueno Días.

Hay mucho post e informacion con comparativas , pero en este caso vamos a intentar que convivan maquinas virtuales con ambas tecnologías.

La solución en mi caso se basa en la forma de trabajo de Virtualbox , este no posee servidor de DHCP y propiedades de las tarjetas de red , simplemente tiene un metodo de creación de interfaces de red virtuales y posteriormente asignas la maquina virtual a dicho interface red virtual .

Ahora he creado una maquina virtual en VMWare y he deshabilitado todos los interfaces de red mediante el gestor "Manage Virtual Networks". Ahora desde la consola de administraciónde VMWare en la opciones de la maquina virtual editamos las opciones de "Interfaces de Red".Seleccionamos "custom" y anotamos el nombre del interface que le corresponde a nuestra maquina virtual.

Necesitamos para este paso poseer un Puente de Red en Windows y el nombre del interface de red de VMWare.

Abrimos el  "Manage Virtual Networks" y vamos a la pestaña "Host Virtual Network Mapping" ,  en el interface que corresponda le asignamos el "Puente minipuerto Mac"

![](images/VirtualNetworkEditor.PNG)

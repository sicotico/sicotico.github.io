---
layout: post
title: "Virtualbox ese gran desconocido"
date: "2007-09-28"
categories: 
  - "sin-categoria"
---

Actualmente estoy trabajando en consultoría y claro terminas por necesitar maquinas virtuales. Yo he tenido que usar Windows XP , portátil de empresa , a mi alrededor todos usan VMware un software no libre y que presenta problemas de recursos , esto empieza a ser la tónica habitual , yo uso VirtualBox en Linux así que busque y lo hay para Windows y MacOS.

La verdad en mi equipo el VMware va a trompicones y el uso del ratón no es agradable. así que aquí estoy el único usando este software maravilloso al que no le encuentro fallos.

El amiguete sghul se ha currado un post para usarlo como [SeamLess Mode](https://www.saghul.net/blog/2007/09/06/virtualbox-15-con-seamless-mode/)

Aquí tenéis el enlace al [post anterior](https://sicotico.wordpress.com/2007/09/26/red-de-virtualbox/) para la configuración de un red virtual con DHCP de la red.

Hoy añadiremos el clonado de discos "vdi" de VirtualBox. Yo actualmente duplico discos "vdi" y la maquina virtual la creo con el asistente dando le como disco el clonado , el cual contiene SO y todo lo que necesito.

Para Windows:

Abrimos un "Símbolo de Sistema"

No movemos a la carpeta de instalacion de VirtualBox

(Necesitamos rutas completas) - Ejecutamos VBoxManage clonevdi <disco origen "vdi"> <disco destino "vdi">

Para Linux:

\- Abrimos una consola , la instalación ha modificado la variable $PATH para los comandos de VirtualBox.

\- Ejecutamos VBoxManage clonevdi <disco origen "vdi"> <disco destiono "vdi">

Para todos los OS

\- Ahora añadiremos al gestor de Discos Virtuales el nuevo disco.

\- Tenemos que usar el asistente para crea un Máquina Virtual nueva y le asociamos el disco clonado.

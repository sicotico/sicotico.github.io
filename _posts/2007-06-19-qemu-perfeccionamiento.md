---

title: "QEMU perfeccionamiento"
date: "2007-06-19"
categories: 
  - "sin-categoria"
---

Me he dado cuenta que no he configurado ninguna opcion de Qemu para activar internet en la MV.

He seguido la documentación de [ubuntu.com](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo?action=fullsearch&value=linkto%3A%22WindowsXPUnderQemuHowTo%22&context=180) "Como hacer WindowsXP bajo Qemu ".

Esta documentación tiene un fallo ,  los paquetes necesarios no poseen forma alguna de crear el "/dev/kqemu"

Solución:

Tras instalar Kqemu ,  localiza  /dev/kqemu , si no está ejecuta estas dos lineas

> **#sudo mknod /dev/kqemu c 250 0 #sudo chmod 666 /dev/kqemu**

No he podido trastear mucho con ella , principalmente porque no he tenido tiempo , cosa de examenes.

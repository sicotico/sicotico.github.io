---
layout: posts
title: "Brother MFC-620CN en Linux"
date: "2008-01-24"
categories: linux hardware
---

Maravilloso multifunción con mil cosas y "cachibaches" pero altamente compatible con Linux . Entremos en faena , necesitaremos un parche para LPR y algo que llaman wrapper los de Brother. Especifico las paginas de los drivers en las que encontrareis para todos los modelos , eso si todos los comando u ordenes estarán pensados para mi modelo .

Pagina del parche [LPR](https://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

Enlace la parche especifico para el [MFC\-620CN](https://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc620cnlpr-1.0.2-1.i386.deb)

Pagina del [Wrapper de CUPS](https://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

Enlace al wrapper especifico para el [MFC\-620CN](https://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC620CN-1.0.2-3.i386.deb)

Ya tenemos todo lo que necesitamos referente a Brother , además necesitamos como dependencia el paquete "csh" y no se resuelve estomáticamente así que habrá que descargarlo con synaptic o por consola.

#sudo apt\-get install csh

#sudo dpkg -i --force\-all mfc620cnlpr-1.0.0-1.i386.deb

#sudo dpkg -i --force\-all cupswrappermfc620cn\_1.0.0-1\_i386.deb CUPS en Debian y derivados no crea usuarios así k el gestor web te pedirá un user y no habrá ninguno en la base de datos , la solución es usar

#sudo lppasswd -a root

y darle una clave con 6 caracteres y un numero como mínimo.

Ya tenemos instalada la impresora , incluso selecciona como por defecto y por usb , si no esta así en vuestro caso editáis las propiedades indicando el puerto de conexión.

Para comprobarlo usamos los administradores de Gnome o KDE o cups vía web:

https://localhost:631

Por si no te ha funcionado , así se limpia el sistema para volverlo a intentar:

Desinstalo todos los paquetes de cups (mantengo: libcupsys2 , libgnomecups1.0-1 y python-cups)

Borro el contenido de cups , mantego /etc/cups

borro las librerias: libbrcompij2.so libbrcompij2.so.1 libbrcompij2.so.1.0

Primer intento de mfc620cnlpr-1.0.2-1.i386.deb

He creado un enlace /var/spool/lpd a /var/spool/ldp

Segundo intento de mfc620cnlpr-1.0.2-1.i386.deb

Instalo cupsys-client (lpadmin)

Creo un enlace /etc/init.d/cups a /etc/init.d/cupsys

Instalo cupswrappermfc620cn\_1.0.0-1\_i386.deb

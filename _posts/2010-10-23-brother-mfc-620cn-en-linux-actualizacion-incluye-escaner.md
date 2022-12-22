---
layout: post
title: "Brother MFC-620CN en Linux (Actualización incluye escaner)"
date: "2010-10-23"
categories: hardware linux
---

En una [entrada](https://luispuente.net/2008/01/brother-mfc-620cn-en-linux/) anterior comentaba como se configura esta multifunción

Desde la versión 10.04 los drivers de Brother se incluyeron en los repositorios oficiales de Ubuntu facilitando la tare de configuración de la impresora. Ahora están simple como marcar el paquete `brother-lpr-drivers-common` y resolver sus dependencias.

La parte del escáner se realiza también por paquetes pero de descarga manual ,  estas son las [instrucciones oficiales](https://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html). Yo he utilizado el "Centro de Software" y no me he encontrado con ningún problema , remarcar que solo vale para `root` y hay que modificar los permisos en las `rules` de `udev` para dejar acceso a usuarios normales.

Para editar el fichero utilizo

- `sudo gedit /lib/udev/rules.d/40-libsane.rules`

Las linea a añadir

- `# Brother scanners ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"`

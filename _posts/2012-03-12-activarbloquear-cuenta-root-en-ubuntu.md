---
layout: single
title: "Activar/Bloquear cuenta root en Ubuntu"
date: "2012-03-12"
categories: linux
---

He necesitado realizar esta operación en mi trabajo y me he dado cuenta de las pocas veces que se indican los contras , así que hoy los voy a poner y.

Como los medicamentos , **efectos secundarios**:

Realizar esta operación incluye una desvinculación de la clave del usuario generado en al instalación con la cuenta root. Más adelante cuando cambies la contraseña de este usuario lo que generas es que sea diferente a la root.

El mantenimiento deberá de incluir la verificación de la nueva contraseña en la cuenta root.

Ahora indico una de las formas más elegantes que he visto para realizar esta tarea.

**Activar cuenta**

Realmente asignarle una contraseña.

`sudo passwd root`

Una vez hecho esto podremos iniciar sesión como root, o iniciar sesión como un usuario normal y comenzar a ejecutar los comandos como root escribiendo el comando su.

**Desactivar cuenta**

Una vez terminadas las tareas que necesitábamos realizar, es conveniente volver a desactivar el super usuario con el flag -l (–lock): `sudo passwd -l root`

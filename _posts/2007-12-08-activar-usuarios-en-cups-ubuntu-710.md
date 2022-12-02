---

title: "Activar usuarios en Cups Ubuntu 7.10"
date: "2007-12-08"
categories: 
  - "sin-categoria"
---

Hace unos días que me puse a manejar mi servidor de cups en remoto y tuve mis problemillas . Al final se resumen en los usuarios que te piden para realizar determinadas operaciones.

Este problema es muy conocido y tiene varias resoluciones , yo explicare la relativa a los grupos de permisos que daría acceso a los usuarios a configurar las impresoras . La idea es establecer usuarios existentes con permisos suficientes para modificar las configuraciones de cups .

Los datos importantes que necesitamos para establecer los permisos es saber cual es el usuario y grupo vinculado a cups y por supuesto a que usuario vas a dar acceso , en este ejemplo utilizaremos al usuario "pepito" y grupo "pepito". Fácil solución abriendo el fichero de configuración :

_#sudo vi /etc/cups/cupsd.conf_

_\# Administrator user group... #SystemGroup lpadmin_ Ahora ya tenemos todos datos que necesitamos , juguemos pues con el fichero del sistema "_/etc/group_"

_#grep -i lpadmin /etc/group_

Su salida es esta :

_#lpadmin:x:108:_

Vemos que el grupo de cups esta totalmente aislado del sistema , hemos de añadir el grupo "user1" y este podrá configurar cups. Tras la modificación el resultado será:

_#grep -i lpadmin /etc/group_

_#lpadmin:x:108:user1_

Pues con esto y una tortilla podemso irnos a dormir con permiso sobre cups para el grupo de usuarios "user1"

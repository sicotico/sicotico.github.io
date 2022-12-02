---

title: "Wordpress en un servidor"
date: "2011-11-29"
categories: 
  - "sin-categoria"
---

Últimamente he entrado en este mundillo y al final he decidido prepararme mi propio "hosting" . Para servicios internos o propios. Haciendo mi primera instalación sobre Ubuntu Server empiezo a ver que de cosas tiene los hosting y el trabajo que conlleva. Esta frase es un guiño al administrador de mi hosting.

Listando los recursos que necesitamos , en lineas generales.

- Apache
- MySQL
- PHP
- PHP-MySQL
- PHPMyAdmin
- FTP

Este es el orden que he utilizado ,  importante para tomar nota de las dependencias que necesitas.

Ahora toca revisar la pagina de Apache y verificar que funciona , cosa sencilla. Determinamos las carpetas que deseamos utilizar y por supuesto dejamos la posibilidad de ampliación así que configuramos un _site_ con su _virtual-host_. En esta caso aplicaremos una resolución por nombres , los puerto para mí son difíciles de recordar.

Nuestro amigo _apt-get_ instalaremos las actualizaciones del sistema y los paquetes necesarios con librerías. Como FTP utilizaré [vsftp](https://help.ubuntu.com/11.10/serverguide/C/ftp-server.html "VSFTP - Guía Ubuntu Server") , ya que es el que viene en la guía de Ubuntu Server.

En base a esta configuración decidí  utilizar como directorio base, para el usuario de ftp , `'/ruta/de/wordpress/'.`

`define(``'FTP_BASE'``,` `'/ruta/de/wordpress/'``);` `// ruta absoluta al directorio raiz donde está instalado WordPress`

Con ese parámetro cree un usuario , de sistema ,que su home fuera ese y active la sincronización de usuario de VSFTP con PAM.

Revisar los permiso del usuario de Apache y del FTP para la dicha carpeta.Por lo que pudiera ocurrir.

Mágia esto ya funciona.

Fuentes:

- [help.ubuntu.com  VSFTP](https://help.ubuntu.com/11.10/serverguide/C/ftp-server.html "VSFTP - Guía Ubuntu Server")
- [ayudawordpress.com FTP](https://ayudawordpress.com/instalar-plugins-y-temas-sin-poner-datos-de-ftp/ "AyudaWordpress FTP")

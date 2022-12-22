---
layout: post
title: "LAMP (Ubuntu , Apache2 , MySQL 4.1 , PHP4 )"
date: "2006-08-17"
categories: linux
---

Buenso dias , como este tiempo he estado jugando con los CMS anotare como se intala los necesario para usarlo:

En KDE exite ADEPT y en gnome Synaptic , seleccionamso los tres paquetes Apache2 , MySQL 4.1 , PHP4 y le damos a aplicar cambios.

Si eres mas consolore pues:

_#sudo apt-get install apache2 php5 mysql-server-(version que prefieras) php5-mysql_ Editamos el fichero php.ini que esta situado en /etc/php4/apache/ o php5/apache según versión y descomentamos la linea "extension=mysql.so" y magia ya tenemos un sistema completo para trabajar con CMS por ahora en la carpeta /var/www

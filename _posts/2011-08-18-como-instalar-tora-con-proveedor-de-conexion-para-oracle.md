---
layout: post
title: "Como instalar TOra con proveedor de conexion para oracle"
date: "2011-08-18"
categories: software
---

Base, Xubuntu 11.04 (**cat /etc/issue**), virtualbox 4.0.12r72916 (**VBoxManage -v**), rpms del cliente de oracle:

  

**oracle-instantclient11.2-basiclite-11.2.0.2.0.x86\_64.rpm  
oracle-instantclient11.2-devel-11.2.0.2.0.x86\_64.rpm  
oracle-instantclient11.2-sqlplus-11.2.0.2.0.x86\_64.rpm**

  

Y por ultimo TOra 2.1.3-1 (**apt-get source tora**).

  

Primero instalamos los rpms del oracle-instantclient desde donde los hemos descargado:

  

**for n in $(ls oracle-\*.rpm); do fakeroot alien $n; done;**

**sudo dpkg -i \*.deb**

  

Esto instala oracle-instantclient en los siguientes directorios:

  

**/usr/lib/oracle/11.2/client64**

**/usr/include/oracle/11.2/client64**

  

Creamos un link simbólico en el directorio /usr/lib/oracle/11.2/client64 que apunte a /usr/include/oracle/11.2/client64:

  

**ln -s /usr/include/oracle/11.2/client64 /usr/lib/oracle/11.2/client64/include**

  

Añadimos las variables de entorno a nuestro perfil de usuario y al perfil por defecto de creación de usuarios:

  

**vi ~/.bashrc**

  

**export ORACLE\_BASE=/usr/lib/oracle/11.2  
export ORACLE\_HOME=$ORACLE\_BASE/client64  
export PATH=$PATH:$ORACLE\_HOME/bin  
export TNS\_ADMIN=/etc/oracle  
export LD\_LIBRARY\_PATH=$LD\_LIBRARY\_PATH:/usr/include/oracle/11.2/client64:****$ORACLE\_HOME****/lib**

  

**vi /etc/skel/.bashrc**

  

**export ORACLE\_BASE=/usr/lib/oracle/11.2  
export ORACLE\_HOME=$ORACLE\_BASE/client64  
export PATH=$PATH:$ORACLE\_HOME/bin  
export TNS\_ADMIN=/etc/oracle  
export LD\_LIBRARY\_PATH=$LD\_LIBRARY\_PATH:/usr/include/oracle/11.2/client64:****$ORACLE\_HOME****/lib**

  

Creamos el directorio /etc/oracle e inicializamos las variables de entorno en esta sesión:

  

**sudo mkdir /etc/oracle**

**. $HOME/.bashrc** o **source $HOME/.bashrc**

  

Instalamos la librería libaio1:

  

**sudo apt-get install libaio1**

  

Y comprobamos si todo ha ido bien ejecutando:

**sqlplus -v**

  

Salida:

  

SQL\*Plus: Release **11.2.0.2.0** Production

  

Ahora ya estamos preparados para instalar Tora, primero descargamos los sources:

  

**apt-get source tora**

  

Comprobamos las dependencias:

  

**sudo apt-get build-dep tora**

  

Construimos el .deb:

  

**cd tora-2.1.3**

**dpkg-buildpackage -us -uc -rfakeroot**

  

Si la compilacion ha ido bien instalamos el .deb generado:

  

**cd ..**

**sudo dpkg -i tora\_2.1.2-1\_amd64.deb**

Comprobamos que funciona ejecutando desde un terminal:

  

**tora**

Para evitar que los updates del sistema nos estropeen lo realizado, ponemos en hold el paquete:

  

**sudo su -**

**echo "tora hold" | dpkg --set-selections**

  

Lo comprobamos con:

**dpkg -s tora**

  

Salida:

Package: tora  
Status: **hold** ok installed  
Priority: optional  
Section: misc  
Installed-Size: 12968  
Maintainer: Debian KDE Extras Team <pkg-kde-extras@lists.alioth.debian.org>  
Architecture: amd64  
Version: 2.1.3-1  
Depends: libqt4-sql (>= 4:4.5.3), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libpq5 (>= 8.4~0cvs20090328), libqscintilla2-5, libqt4-network (>= 4:4.5.3), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.5.3), libstdc++6 (>= 4.5), oracle-instantclient11.2-basiclite  
Description: A graphical toolkit for database developers and administrators  
 Tora features a schema browser, SQL worksheet, PL/SQL editor & debugger,  
 storage manager, rollback segment monitor, instance manager, and SQL output  
 viewer. Via qt4 it can access PostgreSQL and MySQL directly. Any other  
 database systems can be accessed via ODBC.  
Homepage: https://www.torasql.com

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-5469589726853729948?l=tablondesastre.blogspot.com)

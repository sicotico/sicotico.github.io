---

title: "Como instalar Oracle XE en Debian 6.0 de 64bits"
date: "2011-09-05"
categories: 
  - "sin-categoria"
---

Primero obtenemos el material que vamos a necesitar:  
  
**sudo apt-get install ia32-libs**  
  
**sudo apt-get install libaio1**  
  
Obtenemos el Oracle XE versión 32bits:  
  
**wget https://oss.oracle.com/debian/dists/unstable/non-free/binary-i386/oracle-xe-universal\_10.2.0.1-1.1\_i386.deb**  
  
Procedemos a su instalación:  
  
**sudo dpkg --force-architecture -i oracle-xe-universal\_10.2.0.1-1.1\_i386.deb**  
  

Añadimos las variables de entorno a nuestro perfil de usuario y al perfil por defecto de creación de usuarios:

  

**vi ~/.bashrc**

  

export ORACLE\_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server

export ORACLE\_OWNER=oracle

export ORACLE\_SID=XE

export LSNR=$ORACLE\_HOME/bin/lsnrctl

export SQLPLUS=$ORACLE\_HOME/bin/sqlplus

export PATH=$ORACLE\_HOME/bin:$PATH

  

**vi /etc/skel/.bashrc**

  

export ORACLE\_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server

export ORACLE\_OWNER=oracle  
export ORACLE\_SID=XE  
export LSNR=$ORACLE\_HOME/bin/lsnrctl  
export SQLPLUS=$ORACLE\_HOME/bin/sqlplus

export PATH=$ORACLE\_HOME/bin:$PATH

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-4629021316877867468?l=tablondesastre.blogspot.com)

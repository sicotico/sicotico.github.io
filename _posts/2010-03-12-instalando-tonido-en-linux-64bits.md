---
layout: single
title: "Instalando Tonido en Linux 64bits"
date: "2010-03-12"
categories: software
---

Bueno tiene buen pinta , pero claro esta corriendo Windows , esto de tener Linux a 64bits por ahora imposibilita una prueba en un sistema operativo estable.

La instalación ha sido super sencilla , tipo siguiente , siguiente , siguiente .

La instalación en linux 64 si es posible  , pero no hay paquetes para x64 asi que he tirado de foro de soporte de Tonido y hay una explicación muy buena.

Pasos :

descargar el paquete para i686

`wget -c  https://tonido.com/download.php?TonidoSetup_i686.deb`

instalar ia32-libs e i32-libs-gtk

`sudo apt-get install ia32-libs  ia32-libs-gtk`

Forzar la arquitectura para que ignore el Debian Control Arquitecture=x86

`sudo dpkg -i --force-architecture download.php?TonidoSetup_i686.deb`

Iniciar a mano el servicio

`/usr/local/tonido/tonido.sh start`

La salida ha de ser

`Starting Tonido Service:hogar@hogar-desktop:/usr/local/tonido$ nohup: redirecting stderr to stdout`

Acceso via web

`https://:10001`

Como yo lo he instalado en un hosting no tengo interfaz gráfica , y Tonido te dará un mensaje como este:

[![](images/tonido_error_remoto-300x229.png "tonido_error_remoto")](https://luispuente.net/wp-content/uploads/2010/03/tonido_error_remoto.png)

Para solucionarlo he lanzado un tunel SSH

`ssh -l "login" -L 10001:127.0.0.1:10001 "tu server"`

Lanzamos un navegador con [https://127.0.0.1:10001](https://127.0.0.1:10001) , y  activanmos el "Remote Account Creator"

La aplicación , según su creadores , no necesita de Internet , pero para facilitarte las cosas utiliza su propio motor de dynamic DNS (.tonidoid.com), al final de la instalación te solicita conexión a Internet para comprobar que el subdominio esta libre.

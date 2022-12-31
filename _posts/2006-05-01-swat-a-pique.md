---
layout: single
title: "Swat a pique"
date: "2006-05-01"
categories: linux
---

Tras investigar el samba en Ubuntu "Dapper" descubrimos que no usa inetd para el servicio de red , lo cual no llama mucho la atención el problema aparece cuando quieres lanzar un servicio como swat para configurar un samba fácil comodo y bien , aun no he averiguado el servicio de internet ni que entresijos tiene , lo que adelanto es su nombre y que usa la interfaz conocídad de {stop,start,reload,restart} /etc/init.d/networking . Llegados a este punto no podemos usar el antiguo post sobre swat modificando el inet.d para que lanzara el servicio de swat , asi que por ahora lo olvidamos y aunque alguno conteste que esta en los repositorios no va a funcioanr debido a la estructura del sistema.

Así que ahora habrá que funcionar directamente con webmin , aunque sea un poco feo , lo primero es instalar samba , smbclient , smbfs , webmin y webmin-samba . Despues comprobaremos que los usuarios de Unix han sido copiados a samba , usando al opcion de "Convertir usuarios de Unix a usuarios de samba" , tras esto modificamos las opciones por defecto de "Red de Windows" y seleccionamos seguridad "Nivel de usuario, nivel de compartición , servidor clave de acceso , Dominio , Active directory " . Como ya hemos modificado la seguridad ahora si es el momento de crear la compartición en "Crear una nueva compartición de archivo" .

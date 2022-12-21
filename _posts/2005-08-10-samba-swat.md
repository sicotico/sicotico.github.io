---
layout: post
title: "Samba Swat"
date: "2005-08-10"
categories: 
  - "sin-categoria"
---

Sicotico ...

Despues de pegarme mucho con samba decidi usar un entorno mas amigable que es el smb.conf , la verdad tiempo y resultados es salvaje , en apenas 5 minutos tenia ya compartido carpetas e impresoras desde mi linux. Asi que os guste o no aqui lo he dejare escrito .......

instalar samba , smbfs , swat #apt-get install samba samba-common smbclient smbfs swat desactivamso WINS , salvo que semaos profesionales y las necesitemos

{ trukito descubierto: # /usr/sbin/dpkg-reconfigure --priority=low samba no sahorrara recursos no vaya ser que alguien te este quemando los recursos compartidos } las maravillosas herramientas que tiene debian(esto nso actuliza el contendio de inetd , descomenta la linea de swat)

#/usr/sbin/update-inetd --verbose --enable swat

relee la configuracion inetd y activa swat #/etc/inet.d/inetd restart

ahora solo tenemso que arrancar un navegador con la direccion loclahost:901

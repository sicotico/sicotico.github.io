---
layout: single
title: "Cisco VPN en Ubuntu"
date: "2011-07-15"
categories: software
---

Instalar los paquetes

- vpnc
- network-manager-vpnc
- network-manager-vpnc-gnome

Ahora vamos a convertir el fichero pcf de cisco en uno usable por el cliente de cisco de linux. Para ello necesitamos un par de binarios que están en lo paquetes anteriores , pero que los colocan en /usr/share y el path no los reconoce. Copiamos pcf2vpn y /cisco-decrypt a /usr/bin

sudo cp /usr/share/vpnc/pcf2vpn /usr/bin

sudo cp /usr/lib/vpnc/cisco-decrypt /usr/bin

Revisar si tiene spermisos de ejecución , sino

chmod +x  /usr/bin/pcf2vpn

chmod +x  /usr/bin/cisco-decrypt

Ahora cogemos el fichero pcf y lo convertimos

pcf2vpn fichero.pcf > fichero.conf

Lo movemos a la carpeta del cliente de cisco

mv fichero.conf /etc/vpnc

Ahora ya podemos arrancar la vpn

sudo vpnc fichero

Ponemos usuario y password y ya tenemos conexión

sudo vpnc fichero.conf
Enter username for vpn.:
Enter password for usario:
VPNC started in background (pid: 7660)...

Desconectarse

sudo vpnc-disconnect

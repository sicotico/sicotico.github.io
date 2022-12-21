---
layout: post
title: "Configurar la red en Ubuntu Server"
date: "2010-11-01"
categories: linux
---

En este tutorial vamos a aprender como modificar la configuración de red en Ubuntu Server.

La configuración de red se almacena en el archivo /etc/network/interfaces por lo que tendremos que editar este fichero para hacer cualquier modificación.

### DHCP (IP dinámica)

Si tenemos un servidor DHCP en nuestra red y queremos asignarle una dirección IP dinámica a nuestro equipo, debemos editar el  archivo de configuración de las interfaces de red con el siguiente comando:

sudo nano /etc/network/interfaces

Y modificarlo para que quede de la siguiente forma:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

Las dos primeras líneas (en verde) configuran la interfaz de [loopback](https://es.wikipedia.org/wiki/Loopback "Loopback en la Wikipedia"). La primera línea, “auto lo“, indica que se levantará la interfaz de loopback (**lo**) de forma automática durante el inicio del sistema. Mientras que la segunda línea define que la interfaz **lo** es la de loopback.

Las dos siguientes líneas (en azul) configuran la interfaz eth0. La primera línea, “auto eth0“, indica que se levantará la interfaz eth0 de forma automática durante el inicio del sistema. Mientras que la segunda línea define que se usará DHCP para asignarle una dirección IP.

### IP estática (fija)

Ahora bien, si queremos asignarle una dirección IP estática a nuestro equipo, lo más normal al tratarse de un servidor, debemos editar el  archivo de configuración de las interfaces de red con el siguiente comando:

sudo nano /etc/network/interfaces

Y modificarlo para que quede de la siguiente forma:

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
dns-nameservers 80.58.61.250

Las dos primeras líneas son exactamente las mismas que en el caso anterior y definen la interfaz de [loopback](https://es.wikipedia.org/wiki/Loopback "Loopback en la Wikipedia"). Veamos entonces lo que significan las siguientes líneas del archivo:

- auto eth0: indica que se levantará la interfaz eth0 de forma automática durante el inicio del sistema.
- iface eth0 inet static: define que la interfaz eth0 utilizará una IP estática.
- address 192.168.1.3: la [dirección IP](https://es.wikipedia.org/wiki/Direcci%C3%B3n_IP "Dirección IP en la Wikipedia") que se le asigna es 192.168.1.3. Este parámetro es necesario.
- netmask 255.255.255.0: la [máscara de red](https://es.wikipedia.org/wiki/M%C3%A1scara_de_red "Máscara de red en la Wikipedia"). Este parámetro es necesario.
- network 192.168.1.0: la dirección de red.
- broadcast 192.168.1.255: la dirección de _broadcast_. Los paquetes que se envían a esta dirección los reciben todos los equipos de la red.
- dns-nameservers 80.58.61.250: la dirección de un servidor DNS. Podemos elegir un servidor DNS [aquí](https://www.adslayuda.com/index.php?module=FSDns&order=info "DNS de las operadoras").

### Comandos útiles

Una vez que hayamos modificado el archivo de configuración de la red, para que nuestro sistema tome los nuevos valores asignados debemos ejecutar el siguiente comando:

sudo /etc/init.d/networking restart

O bien este otro:

sudo service networking restart

Sin embargo, si tenemos configurada la red por DHCP y, por el motivo que sea, necesitamos pedir una nueva IP podemos ejecutar el siguiente comando:

sudo dhclient eth0

¡Listo! A seguir disfrutando de Ubuntu Server.

Fuente: [Slice of Linux](https://sliceoflinux.com/2009/09/01/configurar-la-red-en-ubuntu-server)

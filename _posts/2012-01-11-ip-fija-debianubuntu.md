---

title: "IP fija Debian/Ubuntu"
date: "2012-01-11"
categories: 
  - "sin-categoria"
---

De esas cosas que siempre se olvidan y busco en internet.

Quiero una ip estática a la que poder acceder desde remoto. Configuro la ip a _mano_ `editando/etc/network/interfaces` haciendo:

sudo nano /etc/network/interfaces

Y la configuración que escribo es la siguiente:

auto lo
iface lo inet loopback
auto eth3
iface eth3 inet static
address 192.168.1.201
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

**Fuente:** [webiform](https://webiforme.blogspot.com/2011/07/instalando-xubuntu-1104.html)

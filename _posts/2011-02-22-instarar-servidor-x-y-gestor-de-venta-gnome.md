---

title: "Instarar servidor X y Gestor de venta Gnome"
date: "2011-02-22"
categories: 
  - "sin-categoria"
---

**Instalación**

`yum groupinstall "X Window System" "GNOME Desktop Environment"`

_Posibles error de dependencias en algunas versiones o en instalaciones muy reducidas_

`Error: Missing Dependency: libgaim.so.0 is needed by package nautilus-sendto`

Las solución es :

`# wget https://mirror.centos.org/centos/5/os/i386/CentOS/nautilus-sendto-0.7-5.fc6.i386.rpm` `# rpm -Uvh --nodeps nautilus-sendto-0.7-5.fc6.i386.rpm`

**Automatizar el inicio según runlevel**

`# cp /etc/inittab /etc/inittab3` `# cat /etc/inittab3 | sed "s/id:3:initdefault/id:5:initdefault/" > /etc/inittab`

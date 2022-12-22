---
layout: posts
title: "Cambiar hostname - CentOS"
date: "2011-02-22"
categories: linux
---

Cuando despliegas maquinas virtuales el nombre de host siempre lo tienes estandarizado , y claro toca cambairlo según corresponda.

**Con reinicio**

cd /etc/sysconfig vi network o cualquier editor que os guste Cambiamos el HOSTNAME salimos reboot

**Sin reinicio**

Utilizamos el comando hostname

Editamos el fiechero /etc/hostname para establer el cambio de forma persistente

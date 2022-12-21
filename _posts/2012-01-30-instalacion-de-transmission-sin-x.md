---
layout: post
title: "Instalación de Transmission sin X"
date: "2012-01-30"
categories: linux 
---

![](images/gearshift.png)

Preparando cosillas en el mi pequeño Proliant se me ocurrió esta. Toda la documentación encontrada sobre este tema data de 2009 y 2010 así que no coincide nada de nada. La web oficial mantiene este wiki que como indica lo va a borrar, por algo será "no vale ni pa pipas". Vamos  a la faena:

- Un sistema sin entorno gráfico , si  uso una Ubuntu Server , no soy lo suficientemente guay para usar Debian  y en el entorno empresarial no he necesitado usar Red-Hat/CentOS.
- Un poco de Internet no nos vendrá mal para aprovechar las bondades del apt-get
- Nuestro amigo vi  , también se puede usar ano  , no soy un radical.

Un simple apt-get nos proporciona la instalación automática

apt-get install transmission.daemon

Trabajando es un servidor remoto se nos presenta la problemática de las lista blanca que viene definida por defecto.Solo para el mismo "localhost" , hay que cambiarla para que en nuestra red local podamos acceder.

vi /var/lib/transmission-daemon/info/settings.json

Original:

"rpc-whitelist": "127.0.0.1"

Modificado:

"rpc-whitelist": "127.0.0.1,192.168.\*.\*"

Usuario por defecto : _transmission_

Password por defecto: _transmission_

Fuente:

[Transmissionbt HeadlessUsage](https://trac.transmissionbt.com/wiki/HeadlessUsage "Transmission HeadlessUsage")

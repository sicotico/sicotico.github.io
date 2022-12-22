---
layout: posts
title: "Truco vmnetcfg en Linux"
date: "2012-11-20"
categories: linux vmware
---

## Esto es el vmnetcfg

\[caption id="" align="aligncenter" width="500"\]![vmware-netcfg](images/8202482721_b5e1de6ebd.jpg "vmware-netcfg") vmware-netcfg\[/caption\]

## Para que sirve el vmnetcfg

Configurar las ip de las maquinas virtuales , es algo necesario si o si . De esta manera puedes saber de antemano que rangos de ips asignar el servidor DHSCP de VMware

## ¿Porque ocurre?

#### Teoría comercial:

Esto de los recortes también llega al software. En este caso se dedican a evitar que lleguemos a funcionalidades que en versiones anteriores  , gracias al cielo no las pueden quitar y solo bloquean el acceso  de forma cutre.

#### Teoría conspiratoria:

Si no te dejo ver los botones que tenias antes seguro que compras una versión de pago

### Solución:

En _/usr/lib/vmware/bin_ descubres que el conocido _vmnetcfg_ se llama en realidad  _vmware-netcfg_ y es un enlace simbólico a _appLoader_. Hay que crear un enlace en /usr/vmware/bin para que sea accesible desde cualquier ruta , no hay icono generado para el en la instalación.

#### Pueden darse dos casos , según versiones del producto:

- No tener el enlace simbólico a appLoader

> - `cd /usr/lib/vmware/bin`
> - `ln -s /usr/lib/vmware/bin/appLoader vmware-netcfg`
> - `ln -s /usr/lib/vmware/bin/vmware-netcfg /usr/bin/vmware-netcfg`

 

-  Tener el enlace al appLoader

> - `cd /usr/lib/vmware/bin`
> - `ln -s /usr/lib/vmware/bin/vmware-netcfg /usr/bin/vmware-netcfg`

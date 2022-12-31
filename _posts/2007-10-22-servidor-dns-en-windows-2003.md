---
layout: single
title: "Servidor DNS en Windows 2003"
date: "2007-10-22"
categories: windows
---

Se instala desde

Control Panel --> Add or Remove Programas --> Add/Remove Windows Components --> Network Services -->Domain Name Server (DNS)

Se accede desde

Administrative Tools --> DNS

Primero creamos una Zona de búsqueda invertida para la resolución de ip - dominio

En "Reverse Lookup Zone" boton derecho "New Zone" seleccionamos "Primary Zone" , el Network ID es nuestra sub red , aceptamos las dos pantallas siguientes del asistente y finalizamos.

ahora crearemos las tablas par ala búsqueda directa de dominio - ip

En "Fordward Lookup Zone" , botón derecho "New Zone" seleccionamos "Primary Zone" , en "Zone Name" corresponde al nombre del dominio principal . Ahora añadimos los host como sub dominios ya que aun no se configurar un dominio master contra un host. Boton derecho "New Host" en "Name" ponemos el nombre del sub dominio y la ip correspondiente al host.

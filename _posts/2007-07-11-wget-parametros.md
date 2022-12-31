---
layout: single
title: "Wget , parametros"
date: "2007-07-11"
categories: linux
---

Esta herramienta es una aplicación en consola para la descarga de archivos , de forma no interactiva.

Esto es lo que uso normalmente.

Parametros:

\-c                            posibilita el resumen de una descarga

\--user-agent=""      identifica a wget como el contenido de las comillas , en este caso no envía identficador

\-r                            descarga recursiva , ademas copia la estructura completa y nos la crea en el destino de la descarga

\-p                            se combina con "-r" para que aun copiando al estructura solo lo haga desde el directorio padre en el que se inicia

\--tries= , -t              intentos antes de mostrar mensaje de error

\--limit-rate=           limita el uso de ancho de banda para la descarga

\--wait=                   pausa entre fichero y fichero

**Ejemplos:** 

wget --wait=20 --limit-rate=20K -r -p --user-agent="Mozilla" -t 20 https://www.luispuente.net

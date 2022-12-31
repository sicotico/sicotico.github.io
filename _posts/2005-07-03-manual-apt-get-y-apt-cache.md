---
layout: single
title: "Manual apt-get y apt-cache"
date: "2005-07-03"
categories: linux
---

Sistema de paquetes Deb

Todos los paquetes deb tienen el siguiente formato: nombre-del-paquete\_version(1.3.34-5).deb

La distribución Debian tiene diversas utilidades para la instalación de paquetes, entre ellas, APT, que permite la instalación de paquetes de forma fácil y rápida, advirtiendo de las dependencias y recomendando paquetes. El sistema APT engloba varios comandos como apt-get, apt-cache, apt-cdrom,…

El fichero /etc/apt/sources.list

Este fichero es imprescindible para la instalación de paquetes con APT. En él se guardan las direcciones de donde APT se descarga los paquetes. Los medios por los que se pueden descargar los paquetes son varios: file(podemos elegir un directorio albitrario de donde bajarnos los paquetes, esto es útil para mirrors locales o carpetas NTFS),de un cdrom,de un servidor web(http), de un ftp, por rsh/ssh.

Vamos a ver un ejemplo:

deb https://http.us.debian.org/debian woody main contrib non-free deb https://non-us.debian.org/debian-non-US woody/non-US main contrib non-free deb-src https://http.us.debian.org/debian woody main contrib non-free

La diferencia entre deb y deb-src es que el primero indica la descarga de paquetes .deb, que son ficheros binarios, es decir, preparados para ejecutarse, mientras que con el segundo podemos descargarnos el código fuente del paquete(usando el comando apt-get source).

La siguiente parte de la línea es el URI, es decir, el tipo de sistema para la descarga, recordemos que existen varios(file,cdrom,ftp,http,rsh/ssh). En este caso es de un servidor web.

Seguidamente escribimos la localización del mirror de paquetes, este caso tenemos varias líneas con diferente localización, esto se debe a que en los Estados Unidoas es ilegal utilizar aplicaciones de encriptación, así que para bajar esos programas, existen líneas especiales que contienen la palabra non-US. Después de la localización, separado por un espacio, se escribe la versión de debian, es válido tanto el alias de la version como en qué estado se encuentra (stable, unstable,testing).

Por último se escriben las secciones de software que usaremos (main, contrib, non-free). Debian organiza los paquetes en varias carpetas segun su licencia.

La sección main agrupa los paquetes en los que su licencia cumple con los criterios de la DGFS(Guías de Debian del Software libre).

La sección contrib agrupa paquetes que tiene una licencia libre pero que sin embargo dependen de otros paquetes que no cumple con las normas del DGFS.

Y por último, la sección non-free contienen paquetes que son de libre distribución pero que sin embargo no cumplen las directrices de la DGFS (no distribuye el código, no se permite redistribuir el código,etc).

Apt-get

El comando apt-get se utiliza para la manipulación de paquetes deb. Permite la instalación de paquetes, borrado, …

apt-get install paquete1 paquete2 …

Instala paquetes.

apt-get remove paquete1 paquete2 …

Borra paquetes.

apt-get source paquete1 paquete2 …

Descarga el código fuente de los paquetes.

apt-get update

Actualiza la lista de paquetes disponibles para instalar.

apt-get upgrade

Instala las nuevas versiones de los diferentes paquetes disponibles.

apt-get dist-upgrade

Función adicional de la opción upgrade que modifica las dependencias por la de las nuevas versiones de los paquete.

apt-get build-dep paquete1 paquete2 …

Instala los paquetes necesarios para la compilación del código fuente de los paquetes.

apt-get clean

Elimina los ficheros que se encuentran en /var/cache/apt/archives y /var/cache/apt/archives/partial. Ahí se encuentran los paquetes que hemos descargado para instalar.

\-d, —download-only

Sólo descarga el paquete, no lo instala.

\-f, —fix-broken

Esta opción es importante, intenta arreglar problemas de dependencias que tengamos en el sistema.

\-s, —simulate

Nos muestra los resultados de la instalación de un paquete.

\-b, —build

Compila el paquete de código fuente que hayamos bajado.

Apt-cache

El comando apt-cache trabaja con la caché de los paquetes. Este comando no manipula el estado del sistema, así que lo pueden usar usuarios normales. Es de gran utilidad ya que nos muestra información valiosa sobre los paquetes.

Algunas opciones más importantes:

apt-cache show paquete1:

Este comando muestra la cabecera de los paquetes. Muestra el desarrollador, las dependencias, una breve descripción del mismo, su tamaño, el nombre del fichero donde se encuentra, entre otros.

apt-cache search texto:

Muestra una lista de todos los paquete y una breve descripción relacionado con el texto que hemos buscado.

apt-cache depends paquete:

Muestra las dependencias de dicho paquete.

apt-cache stats:

Muestra la estadística de el cache.

El fichero /etc/apt/apt.conf

El fichero apt.conf sirve para la configuración por defecto de APT. En el fichero podemos, por ejemplo, darle las órdenes al APT para el uso de un proxy. Podemos encontrar un ejemplo del fichero en

/usr/share/doc/apt/examples/configure-index.gz

Apt-cdrom

El comando apt-cdrom permite añadir nuevos CD-ROM’s al sources.list. Para añadir un cdrom la orden es apt-cdrom add

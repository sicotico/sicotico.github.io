---
layout: single
title: "IE7 en Linux con winetricks"
date: "2010-01-27"
categories: windows linux
---

Lo primero winetricks es un script que automatiza la instalación de librerías y programas de windows con wine , siempre pasa que vamos hacer una prueba y la aplicación que queremos no nos va. claro en windows hay mil mierdas instaladas , así que con este script con GUI nos ayudara enormemente.

Desde la release 20091125 de winetricks es fácil y sencillo instalar Internet Explorer 7 en linux.

Utilizando winetricks instalar IE7 es trivial. No resuelve dependencia de las aplicaciones windows pero con dos clicks se descarga todo de Internet y lo instala.

### Pasos:

Instalar wine , mediante paquetería propia de la distribución (Synaptyc , apt-get , yum ... )

Descargar el script de winetricks

`wget -c  https://www.kegel.com/wine/winetricks`

Dar permisos de ejecución al script

`chmod +x winetricks`

Ejecutar el winetricks , recibe como parámetro el nombre del paquete a instalar, para IE7 son

`winetricks volnum`

`winetricks ie7`

Fuentes:

[wine-reviews](https://www.wine-reviews.net/wine-reviews/winetricks/winetricks-20091125-released-adds-ie-7-support.html)

[Wine HQ - Internet Explorer 7 - AppDB](https://appdb.winehq.org/appview.php?iVersionId=4195)

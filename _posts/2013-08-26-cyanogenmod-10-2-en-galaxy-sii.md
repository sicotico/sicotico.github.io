---
layout: post
title: "CyanogenMod 10.2 en Galaxy SII"
date: "2013-08-26"
categories: android
---

## CyanogenMod 10.2 en Galaxy SII

Ya no hay actualizaciones para este fantástico terminal. Después de 2 años y un cambio de pantalla , va a seguir conmigo , gracias a las CustomROM y para mi  la CyanogenMod es la elegida. Los años que lleva funcionan y el ritmo de actualizaciones es impresionante.

En mi caso viniendo de una StockROM  necesito un nuevo recovery. El oficial de Samsung no sirve para instalar una CustomROM. Ya no se si hay mas recovery , todo el mundo utiliza ClockWorkMod. No debemos de olvidar una versión de Odín ya que va a ser necesaria para dar primer paso. Este proceso se basa copiar el fichero de ROM de CyanogenMod 10.2 y los binarios de aplicaciones de Google en la memoria SD , desde el recovery lanzaremos la instalación de ambas. En lineas generales tenemos la idea .

 

## Recursos necesarios

Descargar  las Gapps , el ROM y el Odín,  publico el [enlace](https://goo.im/gapps "gapps") con el listado de Gapps según versiones de la CyanogenMod , respecto a al ROM esta es la [página de descargas](https://get.cm/?device=i9100 "Cyanogen para i9100 Galaxy SII"). Solo nos falta el [Odín](https://samsung-updates.com/Odin307.zip "Odin 3.07") , esta vez en versión 3.07

Para acceder al recovery se necesita apagar el terminal  y encenderlo presionado Volup + Home + Power

## Pasos

- Copiar el fichero de la CyanogenMod 10.2 y de la Gapps en el raiz de la tarjeta de memoria
- Flashear el CWM mediante Odín
    - Se asigna el fichero del recovery al campo PDA
    - Se marcan exclusivamente
        - Auto Reboot _**Check**_
        - F. Reset Time _**Check**_
- Reiniciar y no configurar nada
- Acceder al recovery y validar el funcionamiento
- Realizar los wipe de cache/data user/cache Davlink
- En el recovery elige instalar zip desde sdcard
- Reiniciar y arrancar por primera vez sin configurar ninguna cuenta
- Accedemos al recover y repetimos procedimiento para las Gapps

Ya tenemos instalada una CyanogenMod 10.2 en nuestro flamante Galaxy SII , y un recovery para las emergencias

---
layout: post
title: "Flashear sin PC un ZTE Skate"
date: "2012-10-24"
categories: android
---

### Con CustomROM no se puede liberar por IMEI es OBLIGATORIO una StockROM

Espero que alguien lea esto antes de actualizar Cyanogen y no le pase lo que a mi , trabar el doble. Primero liberarlo y luego ya lo que quieras.

Llevo unos días con este móvil y la verdad es que me siento atraído con la idea de flashearlo con Roms Custom. Algo nuevo para mi , siempre he usado Stock.

Yo no he instalado los drivers en el Windows 7 así que este método no necesita de conexión móvil <---> pc. Como problema  que te puedes encontrar , yo me lo encontré ,  no arranque la StockRom y no tienes la posibilidad de hacer recovery  para recuperar tu StockRom. Tendrás si o si una ROM cocinada.  La solución es conseguir un backup hecho desde el recovery y cargarlo desde la SD , es un proceso sencillo pero no he dado aun con ningún enlace valido de la  Orange de mi terminal

Los pasos:

- Instalar recovery
- Formatear SD
- Cargar los zip de la ROM a la SD
- Wipe del terminal , desde el recovery
- Instalamos la ROM

Ya tenemos algo más claro el proceso a seguir, ahora toca explicarlos en profundidad.

Lo primero es instalar un Recovery , en este caso usé  CWM  modificado por M0DaCo

- Descargamos : [https://www.mediafire.com/download.php?zdxcak5achuyxsc](https://www.mediafire.com/download.php?zdxcak5achuyxsc)
- Descomprimimos y copiamos la carpeta "image" al raíz de nuestra SD
- El flasheo lo realizaremos desde el propio móvil:
    - Ajustes / Acerca del teléfono / Actualizaciones del sistema / Actualizaciones de la tarjeta de memoria
    - Aceptamos,  tras esto se instalará la recovery.

En mi caso nos e volvía a iniciar al StockROM , no es mayor problema. Desde el recovery se puede montar la tarjeta SD y copiamos en ella los zip de la ROM nueva.

 

Recursos:

- Roms originales para el terminal
    - [https://files.podtwo.com/roms/stock/](https://files.podtwo.com/roms/stock/)
- Ultima versión de Cyanogen unofficial port
    - [https://www.modaco.com/topic/354463-romzte-skate-cyanogenmod-720-stable-android-237-160612/](https://www.modaco.com/topic/354463-romzte-skate-cyanogenmod-720-stable-android-237-160612/)

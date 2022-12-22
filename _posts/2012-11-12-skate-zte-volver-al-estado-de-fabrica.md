---
layout: posts
title: "Skate (ZTE) volver al estado de fábrica"
date: "2012-11-12"
categories: android
---

_Recuperar teléfono basado en el ZTE Skate_

**_Esta guía se ha obtenido de HTCmania y es un reproducción_**

## Instalar en el Skate el recovery original

1. Tenemos que descargarnos [**\>esto<**](https://minus.com/mn7SRmPje/) (**[Enlace alternativo](https://www.mediafire.com/?wynf912bsmpz591)**)y descomprimirlo donde queramos.
2. Luego, arrancamos el Skate y nos aseguramos de que está puesta la "Depuración USB" (Ajustes -> Aplicaciones -> Depuración USB).
3. Conectamos el móvil al PC y miramos que estén TODOS los drivers instalados.
4. Ejecutamos el archivo "install-recovery-windows.bat" que está en la carpeta que hemos descomprimido en el paso 1.
5. Ya tendremos el recovery de serie.

## Instalar lo drivers del Skate correctamente

Ahora bien, puede que cuando nos aparezca la pantalla de "Waiting for device" cuando se te haya reiniciado el móvil. En ese caso, hay que seguir estos pasos. No cancelar el bat

(por cierto, los siguientes pasos son válidos también para aquellas personas que tienen problemas a la hora de instalar el CWM recovery):

1. Descargamos **[\>esto<](https://minus.com/mopTD5NAa/)** (**[Enlace alternativo](https://www.mediafire.com/?8fle7p5s22qycyw)**) y lo descomprimimos donde queramos.
2. Luego abrimos en el PC el Administrador de Dispositivos y veremos como hay un dispositivo que nos sale con un aviso (con un triangulo amarillo).
3. Le damos click derecho y a "Actualizar controlador".
4. Nos dirá que no encuentra el controlador y que lo necesitamos buscar manualmente. Hacemos que lo busque en la carpeta "usb\_driver" que hemos descomprimido con anterioridad, y ya está.
5. Repetimos el proceso de flashear el recovery (el de arriba de este post) y ya no nos dará error (hay que usar el mismo puerto USB, importante).

## Flashear al Skate la ROM original.

Una vez que tengamos el recovery FTM (el de serie) instalado (que ya no nos salga "Waiting for device"), haremos el segundo paso: flashear la ROM original.

1. Para eso, debemos ir **[\>aquí<](https://wwwen.zte.com.cn/endata/mobile/Spain/)** y elegir el móvil que tengamos (el Skate o el Montecarlo).
2. Una vez lo hayamos hecho nos bajamos el "Monte Carlo (o Skate) software online upgrade tool".
3. Lo instalamos, apagamos el móvil y lo arrancamos como si quisiéramos entrar en el recovery con las teclas de \[ENCENDIDO\] + \[VOLUMEN -\].
4. Lo conectamos al PC y seguimos los pasos que nos indica.

Ya lo tendremos con la ROM oficial, recovery oficial, TPT oficial y todo aquello que haya sido modificado.

¡Un saludo!

Fuente:  [**Volver a estado de fábrica**](https://www.htcmania.com/showthread.php?t=360980 "Volver al estado de fábrica")

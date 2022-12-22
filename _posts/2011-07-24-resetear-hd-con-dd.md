---
layout: posts
title: "Resetear HD con dd"
date: "2011-07-24"
categories: linux
---

Siempre ocurre cuando necesitas algo no funciona. Casi casi es mi caso , tenia un disco con una tabla de particiones corruptas , pero funcionaba y puede hacer la copia de seguridad. Después de volcar 900gb por usb 2.0 , unas 15 horas podía trabajar con el e intentar arreglarlo. Se intento redefinir la tabla de particiones para evitar el solapamiento entre ellas pero fue imposible , una de ellas era extendida y no conseguí nada.Tras varios intentos y que el disco no reconociera algunos cambios. La caballería entro en acción y el equipo de limpieza llegó.

dd if=/dev/zero of="dispositivo a borrar" bs=1M 

Si es por seguridad , es mejor poner datos aleatoria en vez de ceros

dd if=/dev/unrand of="dispositivo a borrar" bs=1M

Con bs=1M , marcamos que la acciones de escribir y lectura se realicen en bloques de 1 MB . Se utiliza esta media porque es equilibrio entre velocidad y seguridad , ya que más grande aumenta la tasa de errores de escritura dejando bloque sin escribir.

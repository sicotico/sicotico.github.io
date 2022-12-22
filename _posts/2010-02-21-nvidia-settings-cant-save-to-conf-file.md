---
layout: posts
title: "nvidia settings can't save to conf file"
date: "2010-02-21"
categories: mac hardware
---

Preparando un HTPC para el salón me he encontrado con esto:

`failed to parse existing X config file`

Teniendo en cuenta que no había instalado nada más que el sistema base y los drivers de nvidia. Andaba un poco desconcertado.

En este [foro](https://ubuntuforums.org/showthread.php?t=1101445) hablan del problema y este fue el [post](https://ubuntuforums.org/showpost.php?p=7260881&postcount=18) que me dio la solución.

La aplicaciónde nvidia no es capaz de parsear correctamente el fichero xorg.conf , así  que si lo dejamos reducido a su mínima expresión , fichero en blanco , este nos devuelve

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
At least one Device section is required

Ejecutamos:

- `sudo mv /etc/X11/xorg.conf /etc/X11/xorg.cong-orig`
- `sudo touch /etc/X11/xorg.conf`
- `sudo nvdia-xconfig`
- Eliminamos todo menos sección driver , eliminando lineas vacías  superiores e inferiores.
- `sudo nvidia-settings` o lanzar la aplicación gráfica

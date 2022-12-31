---
layout: single
title: "Servicios en Ubuntu"
date: "2004-03-07"
categories: linux
---

Los servicios o demonios son procesos que se ejecutan automáticamente al arrancar el sistema o al llamarlos y que esperan cualquier petición. Es el caso por ejemplo de Apache, Qmail, SSH, etc. Los servicios normalmente se inician al iniciar el sistema, pero podemos iniciarlo(start), pararlo(stop) o reiniciado, sería así: /etc/init.d/servicio opción.

Para configurar el servicio cuando arrancamos el sistema, podemos usar el comando update-rc.d. Este comando crea o elimina los enlaces a los diferentes directorios de runlevels.

- Para que **no** se inicie automáticamente:
    - `update-rc.d -f servicio remove.`
- Para que se inicie automáticamente:
    - `update-rc.d -f servicio defaults.`

Para añadir un servicio, simplemente creamos el script de nuestro servicio en Bourne Shell Script y lo copiamos al directorio /etc/init.d/.

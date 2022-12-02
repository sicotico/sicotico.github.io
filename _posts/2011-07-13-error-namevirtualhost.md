---

title: "Apache: Error NameVirtualHost"
date: "2011-07-13"
categories: 
  - "sin-categoria"
---

Siempre que juego con el apache me pasa lo de siempre , aparece este error al reiniciar , recargar configuración , etc ...

Error:

Error NameVirtualHost \*:80 has no VirtualHosts

Hoy sin querer me he topado con la solución , y eso que estaba montado un cliente de VNC web , no se que tiene que ver pero me ha iluminado. En el fichero:

/etc/apache2/ports.conf

Comentamos la linea :

Name.....: \*.80

Despues:

#Name.....: \*.80

Fuente: [isp-control.net](https://isp-control.net/forum/thread-7381.html "Error NameVirtualHost")

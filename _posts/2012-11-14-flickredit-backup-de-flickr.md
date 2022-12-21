---
layout: post
title: "FlickrEdit - backup de Flickr"
date: "2012-11-14"
categories: dev
---

## FlickrEdit

Ha vuelto !!!!!! ,  la pesadilla de vaciar este servicio de imágenes. Verificando que tenia todas las fotos descargadas , si he tardado mucho  lo sé, el resultado ha sido negativo. Flump no ha descargado todo y supongo que sera alguna excepción de la aplicación , que no ha sido controlada y además no informa. De milagro no he borrado todas las fotos. Ahora toca el turno de FlickrEdit

Creo que he de hacer dos grupos de este tipo de aplicaciones. Con AdobeAIR y sin el

- AdobeAIR
    - [flump](https://code.google.com/p/onairbustour/ "flump") , ya he hablado de ella [aquí](https://luispuente.net/2011/07/flump/ "Flump descargando Flicker ")
    - [Bulk](https://clipyourphotos.com/bulkr "bulkr") , la hay de pago (14€)
    - [Fotobounce](https://fotobounce.com/ "fotobounce")
- Java
    - [FlickrEdit](https://sunkencity.org/flickredit "flickredit") , la elegida.
    - [Migratr](https://www.callingshotgun.net/about/migratr/ "migratr")

 

\[caption id="" align="aligncenter" width="378"\]![FlickrEdit](images/7.png "FlickrEdit") FlickrEdit\[/caption\]

Detalles iniciales FlickrEdit antes se llamaba Flickr Backup. Respecto a Fotobounce indicar que un instalador de 72 Mb y la necesidad de tener AdobeAIR la convierte en algo muy pesado. También decir que es compatible con Facebook y capaz de descargar la fotos nuestras y en las que estamos etiquetados. Característica no necesaria para nuestros fines.

FlickrEdit no es compatible con OpenJDK , así que la he ejecutado en Windows con una maquina virtual. El despliegue de infraestructura para la operación ,que a mi parecer es simple , ha sido desproporcionado.

He necesitado

- Maquina virtual con Windows
- Java Runtime
- Samaba

Aunque utilizo Linux la flata de compatibilidad con OpenJDK me dolido. El camino más fácil a sido crear una maquina virtual con Java instalado. En mi equipo he habilitado un recurso compartido para las imágenes.  Desde la máquina virtual he montado el recurso como si de una unidad e red se tratase , para maximizar al compatibilidad con FlickrEdit.  Ahor aya podemos ejecutar el proceso de descarga de imágenes.

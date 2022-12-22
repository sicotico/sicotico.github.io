---
layout: posts
title: "Rendimiento HDD y NFS"
date: "2012-04-17"
categories: linux
---

Tras el análisis de la red , y ver que tengo la red a 1000 funcionando. Toca las pruebas al disco duro , y al recurso NFS.

Primero probamos el recurso NFS montado en /media/nfs

dd if=/dev/zero of=./prueba.dat bs=8k count=128k
131072+0 registros leídos
131072+0 registros escritos
1073741824 bytes (1,1 GB) copiados, 16,5603 s, 64,8 MB/s

Ahora en el disco nativo

dd if=/dev/zero of=./prueba.dat bs=8k count=128k
131072+0 registros leídos
131072+0 registros escritos
1073741824 bytes (1,1 GB) copiados, 7,40915 s, 145 MB/s

El NFS esta dando unas tasas decente de trasferencia , con autenticación y sincronización al momento.

_Nota: Todo se ha realizado desde terminal y con rutas relativas_

Ahora desde Dolphin probamos a copiar desde el NFS al disco fijo.

- Un fichero de 1,2GB obtenemos 42MB/s
- Un fichero de 4,2GB obtenemos 55MB/s

Esta mejora de velocidad compara con el anterior post se debe a deshabilitar los efectos de KDE 4.x. El cambio de rendimiento del escritorio ha sido increíble pero en las operaciones sobre disco duro  aun se nota más mejora.

Para esta configuración he utilizado este [post](https://xenodesystems.blogspot.com.es/2011/02/como-mejorar-el-rendimiento-de-kde-4xx.html "Cómo Mejorar el Rendimiento de KDE 4.x.x ") de [Xenode System](https://xenodesystems.blogspot.com.es/ "Xenode Systems")

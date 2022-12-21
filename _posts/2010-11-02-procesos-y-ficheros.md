---
layout: post
title: "Procesos y ficheros"
date: "2010-11-02"
categories: linux
---

Hoy se me ha bloqueado un disco con un error de escritura , era fat32 , y no conseguía desmontarlo por medios "normales"

- Mediante escritorio
- Con el comando sudo umount /dev/...

Buscando un poco encontré dos forma de atajar el problema y tres métodos para realizarlo.

**Formas:**

Lo primero son las forma de actuación  primero y más elegante buscar el proceso que lo mantiene ocupado y segundo método desmontar , forzando umount , el dispositivo.

**Métodos:**

_fuser_ relaciona ficheros y procesos , a sabiendas que todo dispositivo en linux es uno , nos proporciona una interfaz muy manejable

$fuser -m <dispositivo de bloques>

y nos devolverá el PID de un proceso , el que esta utilizando nuestro preciado recurso.Intentamso obtener algo mas de info con un simple ps

ps uax | grep <PID>

_lsof_ lista fichero abiertos, como dijimos antes , solo debemos buscar nuestro dispositivo y en este caso ni eso  , simplemente con el directorio donde esta montado nos valdría

lsof | grep <directorio de montaje>

_umount_ utilidad para desmontar dispositivos de bloques_,_ en este caso utilizaremos el parámetro para forzar la operación "-l" de lazy_._

sudo umount -l <dispositivo de bloques> o <directorio de montaje>

---
layout: single
title: "Headers HTTP sin informacion"
date: "2012-12-04"
categories: linux
---

# Apache

Headers HTTP , ese gran desconocido. Hoy toca anotar algunas modificaciones del Apache que permiten controlar la información mostrada.

En [systemadmin.es](https://systemadmin.es "systemadmin.es") te explican las directivas para conseguirlo y yo aclaro el caso para Ubunbtu.

El fichero sobre el que trabajaremos es:

/etc/apache2/conf.d/security

Y las directivas que involucran los datos de las Headers HTTP  son

- **ServerTokens**
- **ServerSignature**

Si utilizar el paquete binario de Ubuntu veras el fichero comentado con los posibles valores  de estas directivas. Las recomendadas son

- **ServerTokens  Prod**

`ServerTokens Full` (or not specified)

Server sends (_e.g._): `Server: Apache/2.4.1 (Unix) PHP/4.2.2 MyMod/1.2`

`ServerTokens Prod[uctOnly]`

Server sends (_e.g._): `Server: Apache`

`ServerTokens Major`

Server sends (_e.g._): `Server: Apache/2`

`ServerTokens Minor`

Server sends (_e.g._): `Server: Apache/2.4`

`ServerTokens Min[imal]`

Server sends (_e.g._): `Server: Apache/2.4.1`

`ServerTokens OS`

Server sends (_e.g._): `Server: Apache/2.4.1 (Unix)`

- **ServerSignature Off**

La opción `Off` , es la de por defecto en Apache , pero no en Ubuntu. Esto suprime la linea del pie , esta opción es compatible con  Apache-1.2 e inferiores. La opción `On`  simplemente  añade una linea al pie con  la versión del servidor , el contenido del `ServerName`  y el Email  referenciado a la directiva  `ServerAdmin`.

 

 

# PHP

Como detalle final  queda la información del PHP instalado y que por razones obvias no se configura en Apache. Asiq ue el fichero a revisar ahora es el php.ini.

- **expose\_php = On (Antes)**

Debemos deshabilitar esta directiva ya si no mostrará ningún tipo de mensaje.

- **expose\_php = On**

Siguiendo unas indicaciones de buenas practicas

## Fuentes:

- [Como eliminar la información sobre versiones de los headers HTTP](https://systemadmin.es/2009/01/como-eliminar-la-informacion-sobre-versiones-de-los-headers-http "como eliminar la informacion sobre versiones de los headers http")
- [ServerTokens Directiva](https://httpd.apache.org/docs/current/mod/core.html#servertokens "servertokens")
- [ServerSignature Directiva](https://httpd.apache.org/docs/current/mod/core.html#serversignature "serversignature")

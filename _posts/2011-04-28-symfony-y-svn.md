---
layout: post
title: "Symfony y SVN"
date: "2011-04-28"
categories: dev
---

Hace poco he recuperado un proyecto completo de Symfony desde Netbeans con el plugin de SVN , bastante sencillo. Deje todos los valores por defecto y alguno lo podía haber cambiado.

Ejemplo la descarga del proyecto me genero una carpeta nueva en al ruta "trunk" así que hubo que revisar el VirtualHost de Apache y modificar el alias de "sf" y el DocumentRoot

Tras revisar todo y descubrir que no tengo ni idea de configurar un apache en condiciones solo conseguía una pagina en blanco.

Error localizado en los logs de Apache (primero sitio a revisar):

_the cache directory is missing: ncaught exception 'sfCacheException' with message 'Failed to make cache directory "/home/user/www/proyecto/cache/frontend/prod/config" while generating cache for configuration file "config/config\_handlers.yml".' in /home/user/www/proyecto/cache/frontend/prod/config/symfony-1.4.1/lib/config/sfConfigCache.class.php :340_

_Create the cache direcotry manually, because symfony doesn't have the rights to create it..._

Solución:

Cambiar el propietario de la carpeta al usuario por defecto de Apache , el SVN descargo el proyecto entero con el login del usuario concurrente y Apache en Ubuntu corre con el usuarios www-data.

sudo chown www-data:www-data -R  /home/user/www/proyecto

Detalles a revisar par ala próxima vez "CheckList":

- Apache site
- DocumentRoot
- El alias de "sf"
- Permisos

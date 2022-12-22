---
layout: posts
title: "Copias de DB en phpMyAdmin"
date: "2007-07-03"
categories: dev
---

Bueno, voy a explicar como hago un respaldo de una base de datos. Específicamente del contenido , es requisito indispensable crearla a mano en blanco. Yo utilizare phpMyAdmin:

**Primero necesitas [phpMyAdmin](https://www.phpmyadmin.net/) el cual es una Herramienta Administrativa de Base de Datos MySQL.**

1. Abre phpMyAdmin
2. Pulsa en Bases de Datos
3. Pulsa tu base de datos
4. Pulsa Export (arriba derecha)
5. En Export - Pulsa Select All
6. Selecciona SQL
7. Selecciona en la sección de Estructura:
    1. Add DROP TABLE /DROP VIEW
    2. Add IF NO EXISTS
    3. Añadir el valor AUTO\_INCREMENT
    4. Usar "backquotes" con tablas y nombres de campo
8. Selecciona en la sección de Data:
    1. Completar los INSERTS
    2. Usar hexadecimal para campos binarios Tipo de exportación

9. Marcamos Enviar (generar un archivo descargable)
10. Rellenamos "Plantilla del nombre del archivo" con el nombre de nuestro fichero
11. En <b>Compression</b> especifica tu opción.(yo no comprimo)
12. Pulsa Continuar.

**Como restaurar la Base de Datos usando phpMyAdmin.**

1. Abre phpMyAdmin
2. Pulsa en Databases
3. Pulsa en tu base de datos
4. Pulsa en SQL
5. Utiliza el boton de busqueda para localizar el archivo de tu base de datos.
6. Pulsa Continuar.

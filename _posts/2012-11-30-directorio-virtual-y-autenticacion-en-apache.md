---
layout: posts
title: "directorio virtual y autenticación en Apache"
date: "2012-11-30"
categories: linux
---

## directorio virtual

directorio virtual , estas palabras me hace recordado una etapa de mi vida con Apache , y que sea rápido porque esto es "para ayer". Estaba entretenido montado unos directorios virtuales y he recurrido a mis almacén de notas

**Viejos Post:**

- Truco Apache
- Apache2: directorio virtual

Bien ya tengo tengo un poco de seguridad , sin pasarse  ,  y los directorios. Todo fácil y sencillo en pequeñas unidades. Ahora toca unirlo todo.

Tras generar el directorio virtual con Webmin y ver que se  dejaba demasiados parámetros en el tintero  , atacamos a la directivas de forma manual.  La disyuntiva entraba cuando a retocar al configuración de la seguridad. Las configuraciones las podíamos hacer utilizando el típico de ._htaccess_ o bajo la directiva de _<Directory>_.  Por versatilidad he utilizado _.htaccess_ . A mi pareces es más fácil colocar el fichero en todos los directorios a proteger y estable un fichero de contraseñas fijo para todos.

Tal como esta indicado no funcionaría nunca , se ha de corregir la directiva :

_AllowOverride none_ por _AllowOverride AuthConfig_

El resultado final:

`Alias /prueba "ruta absoluta" <Directory "ruta absoluta"> Options Indexes MultiViews AllowOverride AuthConfig Order allow,deny Allow from all`

 

Fuente: [Authentication and Authorization](https://httpd.apache.org/docs/2.2/howto/auth.html#theprerequisiteshttps:// "Authentication and Authorization")

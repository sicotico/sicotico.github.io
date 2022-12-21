---
layout: post
title: "Redireccion .htaccess"
date: "2009-08-28"
categories: linux
---

He cambiado la redirección , estaba con un sistema de HTML estatico y no me generaba correctamente el sitemap ,asi que evolucionamos a modRewrite , he ganado caracter profesional

[html-redirigir-una-pagina](https://luispuente.net/2007/12/06/html-redirigir-una-pagina/)

He creado un .htaccess con el siguiente contenido:

`RewriteEngine on RewriteRule ^/$ /wp/` **Actualización** Al final esto ha fallado ,  la idea me pareció bueno así que que seguimos en la misma linea `# INICIO redirigir RewriteEngine on RewriteCond %{REQUEST_URI} !/wp$ RewriteCond %{REMOTE_ADDR} !^123.123.123.123 RewriteRule $ /wp [R=302,L] # FIN redirigir`

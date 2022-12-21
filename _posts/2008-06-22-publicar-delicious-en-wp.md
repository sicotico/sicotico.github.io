---
layout: post
title: "Publicar del.icio.us en WP"
date: "2008-06-22"
categories: dev
---

Buenas hoy he encontrado como publicar los marcadores sin necesidad de plugins en wp , básicamente la idea dar usuario a del.icio.us y el lo publicara , lo malo es que te pide muchos datos un poco cripticos

Paso a paso

Conectamos a del.icio.us --> login --> settings --> daily blog posting--> add a new thingy

> Al estar conectado a del.icio.us, haz click en el enlace a settings en la esquina superior derecha, y selecciona daily blog posting bajo el subtítulo “experimental”. Luego haz click en el enlace a add a new thing
> 
> job\_name: \[cosa tuya, tú decides como llamarás a esta "thingy"\] daily blog posts
> 
> out\_name: el nombre de usuario para tu blog
> 
> out\_pass: la contraseña para tu blog
> 
> out\_url: \[esto dependerá del software que ocupes para bloguear\]
> 
> para [WordPress](https://wordpress.org/ "WordPress > Free blog tool and weblog platform"): https://\[dirección\]/xmlrpc.php
> 
> para [Movable Type](https://www.sixapart.com/movabletype/ "Movable Type: Publishing Platform for Business Blogs and Professionals"): https://\[dirección\]/mt-xmlrpc.cgi
> 
> out\_time: \[cuando quieras que los enlaces sean publicados a tu blog; 0=8pm EST
> 
> out\_blog\_id: dejar en blanco para WordPress, puede necesitar agregar un número (p. ej: 1) para otros programas para weblogs
> 
> out\_cat\_id: \[en qué categoría quieres que se publiquen tus enlaces de del.icio.us; puedes crear una categoría para tus enlaces, ver que "id" tiene y luego ingresarla aquí\]
> 
> Traducido por [yukei](https://www.yukei.net/2006/04/enlaces-de-delicious-en-tu-blog/) de  [How to back up del.icio.us bookmarks on your blog - Lifehacker](https://www.lifehacker.com/software/delicious/how-to-back-up-delicious-bookmarks-on-your-blog-159861.php "How to back up del.icio.us bookmarks on your blog - Lifehacker"), contenido propiedad de [Gawker Media](https://www.gawker.com/advertising/terms-of-use.php "Gawker Media: Terms of Use") bajo [licencia Creative Commons](https://creativecommons.org/licenses/by-nc/2.0/ "Atribución-NoComercial")

Es una obra derivada y se licencia como pide el autor en:

[CC Atribución-Licenciar Igual 2.0](https://creativecommons.org/licenses/by-sa/2.0/es/)

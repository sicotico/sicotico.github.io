---
layout: single
title: "La mudanza no estaba tan cerrada como creía"
date: "2010-10-12"
categories: dev
---

Llevo un par de post en el nuevo servidor y he descubierto cosas un poco raras. El fichero htaccess de mi antiguo servidor tenia unas reglas un poco raras.

`RewriteEngine On RewriteBase /wp/ RewriteCond %{REQUEST_FILENAME} !-f RewriteCond %{REQUEST_FILENAME} !-d RewriteRule . /wp/index.php [L]`

Estas lineas corresponde a la sección Opciones --> Enlaces permanente . En la versión anterior de mi Wordpress pedía modificar el .htaccess para generar las url bonitas , o como dicen ellos personalizar los enlaces permanentes. Yo simplemente las agregué de forma manual y todo funcionando.

A día de hoy Google estaba mandando a los usuarios a mi anterior blog y eso no podía dejarlo estar , aunque solo lo lea yo , más bien porque solo lo leo yo debe funcionar correctamente , "solo hay una forma de hacer las cosas y es correctamente".

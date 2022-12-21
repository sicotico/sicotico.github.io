---
layout: post
title: "Añadir tipos validos a Wordpress 3.x"
date: "2011-06-10"
categories: dev
---

Odio este mensaje ,  no conseguía tiempo para arreglarlo. Intente usar algún plugin de gestión de MIME-Type pero no funcionaba y bloqueaban el comportamiento normal.

[![](images/error_upload.jpg "error_upload")](https://luispuente.net/wp-content/uploads/2011/06/error_upload.jpg)Al final la solución pasa por edita el function.php de wpinclude y en la función de mime aceptado añadir una liena por mime-type , utilizando esta sintaxys

 'extensión\_1 | extensión\_2 | extensión\_3' => ' mimetype'

Las comillas son simples , para más detalle la de al lado del cero

Yo he tenido que añadir los comprimidos

// Compresse formats
'rar|rev|r0' => 'application/x-rar-compressed',
'zip' => 'application/zip'

Nota para navegantes , no lo he hecho en este blog , así que no intentéis subir exploits con formatos comprimidos. Gracias

 

Fuentes:

[electronicholas.com](https://electronicholas.com/2010/08/how-to-force-wordpress-3-to-accept-different-upload-file-types/ "How to force Wordpress 3 to accept different upload file types")

[Behindtheblog](https://blogs.voxeo.com/behindtheblog/2008/10/28/how-to-allow-the-upload-of-newer-file-types-not-listed-in-wordpress/ "How to allow the upload of newer file types not listed in Wordpress")

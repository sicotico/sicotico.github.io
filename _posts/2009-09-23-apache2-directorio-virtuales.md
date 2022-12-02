---

title: "Apache2: Directorio Virtuales"
date: "2009-09-23"
categories: 
  - "sin-categoria"
---

Como compartir caprpetas disjuntas en tu disco , en un solo servidor web sin dominios ni enlaces.

Con una instancia de Apache , varios directorios virtuales y tantos alias como sean necesarios.

el fichero httpd.conf , dentro del modulo `alias_module`

`Alias /prueba "ruta absoluta"`

`Options Indexes MultiViews AllowOverride None Order allow,deny Allow from all`

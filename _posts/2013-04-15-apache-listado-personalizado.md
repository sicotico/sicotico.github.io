---
layout: post
title: "Apache Listado personalizado"
date: "2013-04-15"
categories: linux
---

# **Apache Listado personalizado**

Hay muchas forma de hacer Apache Listado personalizado personalizado , yo me he decantado por Webmin. No he encontrado mucha información y la traducción al castellano no tiene ningún sentido , así que recomiendo ponerlo en ingles al menos para configurar lo.

\[caption id="" align="aligncenter" width="640"\]![Apache Listado personalizado](images/8436843360_074548b2d6_z.jpg "apache_list_personalizado") Apache Listado personalizado\[/caption\]

 

A nivel de configuración en el site de Apache que elijas sería así:

		Options Indexes MultiViews
		AuthName "Titulo para mostrar automaticamente"
		AuthType Basic
		AuthUserFile .htpasswd
		require valid-user
		AllowOverride None
		IndexOptions SuppressHTMLPreamble FoldersFirst
		IndexIgnore \*oto\*
		HeaderName "/header.shtml"
		ReadmeName "/footer.html"

		Order allow,deny
		allow from all

La parte de estilos , cabecera y pie son Apache Directory Listing

                IndexOptions SuppressHTMLPreamble FoldersFirst
		IndexIgnore \*oto\*
		HeaderName "/header.shtml"
		ReadmeName "/footer.html"

### Notas:

El parametro _ReadmeName_ hace referencia al _Footer_ de la web y la traducción en el Webmin es tambien infumable.  No se como recordarlo para otras veces.

Respecto a lo demas , hay mil de opciones para ahbilitar , por ejemplo iconos personalizados imagenes de fondo y mucho CSS para que quede más bonito.

### Fuentes:

[Apache Doc IndexOptions](https://httpd.apache.org/docs/2.2/mod/mod_autoindex.html#IndexOptions "Apache Docs IndexOptions") [Apache Doc IndexIgnore](https://httpd.apache.org/docs/2.2/mod/mod_autoindex.html#IndexIgnore "Apache Docs IndexIgnore") [Apache Doc HeaderName](https://httpd.apache.org/docs/2.2/mod/mod_autoindex.html#HeaderName "Apache Docs HeaderName") [Apache Doc ReadmeName](https://httpd.apache.org/docs/2.2/mod/mod_autoindex.html#ReadmeName "Apache Docs ReadmeName")

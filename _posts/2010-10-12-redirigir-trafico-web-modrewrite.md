---

title: "Redirigir trafico web modRewrite"
date: "2010-10-12"
categories: 
  - "sin-categoria"
---

Siguiendo al política de hacer las cosas bien y solucionado los flecos de la mudanza de hosting me he empapado de conocimiento con esas fuentes de abajo del post.

\# BEGIN WordPress
#<IfModule mod\_rewrite.c>
RewriteEngine On
RewriteBase /wp/
RewriteCond %{REQUEST\_FILENAME} !-f
RewriteCond %{REQUEST\_FILENAME} !-d
RewriteRule ^(.\*)$ https://luispuente.net/$1 \[R=301,L\]
#RewriteRule . /wp/index.php \[L\]
#</IfModule>

# END WordPress

Es un poco más complicado que los ejemplo que puedes encontrar en internet , esto incluyen una regla anterior generada por Wordpress para crear de forma elegante los enlaces permanentes. Cuando lo entiendes resulta simple modificar la regla para que te redirija al nuevo host. No se puede eliminar porque Google tiene los enlaces indexados con el directorio "/wp/" , asi que los accesos realizados mediante buscador tendrán esa forma.

Los parámetros que he utilizado son R=301  , para mudanzas permanentes , informas al buscador de la nueva situación. La "L" ignora el resto de reglas

Una chuleta:

\[flickr size="small"\]https://www.flickr.com/photos/12949201@N08/5599422795\[/flickr\]

**Fuentes:**

Rudy Girón [Redirigir las visitas de un sitio a otro usando .htaccess](https://www.rudygiron.com/ciberspacio/redirigir-las-visitas-de-un-sitio-a-otro-usando-htaccess.html) Ayudawordpress.com [Mudar WordPress (Dominio y/o Directorio) (II)](https://ayudawordpress.com/mudar-wordpress-dominio-yo-directorio-ii/) [Apunte sobre las redirecciones 301](https://ayudawordpress.com/apunte-sobre-las-redirecciones-301/) Hello Google [Redirección 301: Cómo cambiar de nombre de dominio sin perder PageRank ni posicionamiento](https://www.hellogoogle.com/301_cambiar_dominio_page_rank/) EmezetaBlog [Redirección 301 con ModRewrite](https://www.emezeta.com/articulos/redireccion-301-cambiando-de-url) dnQna [Muda tu dominio sin perder ni pagerank ni backlinks](https://dnqna.com/seo/muda-tu-dominio-sin-perder-ni-pagerank-ni-backlinks/)

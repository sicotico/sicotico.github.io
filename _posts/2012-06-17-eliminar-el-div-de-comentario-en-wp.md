---
layout: posts
title: "Eliminar el div de comentario en WP"
date: "2012-06-17"
categories: dev
---

En el fichero _page.php_ tenemos el montaje de la pagina , y podemos deshabilitar la capa de comentarios , sin deforma el tema

Como está

 php comments\_template( '', true );

Como lo debemos de dejar

 php comments\_template( '', true );

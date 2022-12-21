---
layout: post
title: "Botonoes sociales"
date: "2012-07-24"
categories: dev
---

Esto es una de las cosas más simples pero como lo hago muy de vez en cuando  , al final lo he tenido que apuntar. Tengo un web en la que quiero empezar a "socializar" las redes y el camino son los botones , en este caso los oficiales. A los que me refiero son lo de **me gusta**  o **_sígueme_**  ,  mi intención es integrarlo en una web mediante el uso de una capa  y un posicionamiento. Yo lo he utilizado en Wordpress y he utilizado el fichero _footer.php_ del tema que estaba usando. Modificar este ficheros ha sido por razones simples , quiero que aparezcan en el pie de la pagina y por tanto su código deberá de estar en ese fichero .

El prime rpaso es acceder a los recuros que las diferentes redes nos proporcionan. Tanto [Facebook](https://twitter.com/about/resources/buttons#follow "botones twitter") como [Twitter](https://twitter.com/about/resources/buttons#follow "botones twitter")  poseen un generador de código según gustos del usuario. Para facebook no he utilizado las instrucciones ya que requería modificar varios fichero , el f_ooter.php_ y el _header.php_ para introducir código script en el head.

### Facebook

 

[Seguir a @ashesofoblivion](https://twitter.com/ashesofoblivion)
<script type="text/javascript">// < ![CDATA[ !function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id))js=d.createElement(s);js.id=id;js.src="//platform.twitter.com/widgets.js";fjs.parentN ode.insertBefore(js,fjs);}}(document,"script","twitter-wjs"); // ]]></script>

 

<script type="text/javascript">// < ![CDATA[ (function(d, s, id) { var js, fjs = d.getElementsByTagName(s)[0]; if (d.getElementById(id)) return; js = d.createElement(s); js.id = id; js.src = "//connect.facebook.net/es_LA/all.js#xfbml=1"; fjs.parentNode.insertBefore(js, fjs); }(document, 'script', 'facebook-jssdk')); // ]]></script>

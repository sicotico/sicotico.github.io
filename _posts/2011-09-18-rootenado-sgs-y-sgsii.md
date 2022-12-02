---

title: "Rootenado SGS y SGSII"
date: "2011-09-18"
categories: 
  - "sin-categoria"
---

Pues bien explicado en el post , necesito permisos de root para liberar los dos terminales. Voy a utilizar el método de flasear un kernel modificado , o "pre-root".  De todos los que he visto solo he utilizado el **_amonRa_** en mi vieja HTC Hero y el _**CF-Root**_ en la SGS. Este método consiste en flashear con Odin el terminal utilizando un solo un fichero , el Kernel o PDA , y evitando reparticionar.

EL CF-Root tiene su base en el foro XDA-Developers , tiene dos hilos uno con las versiones para SGS y otro para SGSII . Haciendo una introducción la versión 3.7 es la última para SGS y la 4.1 para SGSII.

Hilos de XDA-Developers:

- [Para SGS](https://forum.xda-developers.com/showthread.php?t=788108 "CF-Root para SGS")
- [Para SGSII](https://luispuente.net/2011/09/recuperando-contenido-de-archivos-eliminados-en-linux/ "CF-Root para SGSII") 

Un domingo de recuperación significa hacer cosas con mis manos. Me veo capaz de  liberar mi móvil. Hoy toca liberar dos terminales y actualizarlos.

Un rato de búsqueda en google dio luz sobre rootear una SGS , 2.3.4 JVQ + CF-Root.

Realmente después de encontrar este [manual](https://www.return222.com/2011/07/mega-tutorial-guia-completa-y-todo.html "Mega tutrial SGSII") , hay pocas cosas que aclarar.

Mi terminal necesita Galaxy SII liberarse , y para ello el requisito es tener permisos de root. Hasta hoy no había libera un Android , lo que por lógica debiera ser bastante fácil ya que las limitaciones de SIM Lock están integradas en el sistema operativo y hay  muchos desarrolladores para que no se hayan topado con la correspondiente sección de código.

Hace un tiempo localicé en el market unas aplicaciones que eliminan esta limitación y pedía ser root. Para ello utilizo el CF-Root y mi terminal traía la versión KG1 así que el kernel que necesitaba era:

`CF-Root-SGS2_XX_OXA_KG1-v4.1-CWM4`

Utilizamos el Odin para flashear

\[flickr size="medium"\]https://www.flickr.com/photos/12949201@N08/6159628720/\[/flickr\]

Con esto ya tenemos permisos y utilizamos la app [![](images/45_avail_market_logo2.png)](https://market.android.com/details?id=com.helroz.galaxysunlock&feature=related_apps) para liberar el terminal SGS o SGS II .

Ahora , ya tranquilo y probando que mi tarjeta funciona sim funciona correctamente actualizamos a 2.3.4 KH3 con el CF-Root correspondiente.

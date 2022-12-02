---

title: "JavaScript en WordPress"
date: "2010-01-03"
categories: 
  - "sin-categoria"
---

Ultima modificación para el Adsens de Google , lo he inserado en el fichero sidebar.php . Me he desecho de los saltos de linea y de unos comentarios un poco incordiones y he situado las lineas de JS dentro de las etiquetas de PHP mediante echo "...." . Para que saliera correctamente hay que cambiar todas las comillas dobles por simples , las dobles son las usadas el echo de PHP para detectar el literal. El resultado es algo asi :

`echo "<script type='text/javascript'>google_ad_client = 'xxxxxxxx';/* 300x250, creado 2/01/10 */google_ad_slot = 'xxxxxx';google_ad_width = 300;google_ad_height = 250;</script>"; echo "<script type='text/javascript'src='https://pagead2.googlesyndication.com/pagead/show_ads.js'></script>";`

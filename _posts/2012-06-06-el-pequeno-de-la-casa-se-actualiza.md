---
layout: post
title: "El pequeño de la casa se actualiza"
date: "2012-06-06"
categories: hardware
---

Después de meses por casa y otros tanto dando servicio , el equipo estaba maduro y tocaba una actualización. Empecé el proceso de mejora continua , el primer paso el hardware y el segundo el software.

La memoria RAM se me antoja costa si quiero virtualizar , así que se marco como prioridad. La compatibilidad es reducida por el modelo de memoria que lleva (ECC) , así que localicé un módulo de 4 GB y me tiré a la piscina.  Por limitaciones de la infraestructura solo puede llevar 8 GB de RAM el equipo así por esta vía no se va a vitaminar más. Como siempre he tardo media hora en sacar el dichoso cable

![](images/cable_proliant.jpg "Cable Proliant")

Por lo demás con las herramientas que vienen con el equipo se desmonta en un par de minutos.

La segunda parte corresponde al software y en especial al sistema operativo. Aunque soy de los que habilitan la instalación de actualizaciones automáticas el cambio de versión requiere un espacio en disco que no tenía. Actualmente sigue corriendo el sistema operativo en el  mismo pincho USB de 4GB TDK y para el proceso hace falta 1,6 GB de espacio y libre , se antojaba difícil "inventar  espacio ". La solución pasa por un cambio de soporte , con un pincho más grandes todo solucionado  , pero una instalación limpia es mucho trabajo  , ya la tengo configurada y no me apetece mucho repetir el proceso. La idea vino a mi mente , utilizar la  copia binaria del USB TDK. Perfecto , con un dd tengo una imagen binaria del disco:

sudo dd  if=/dev/sdb of=tdk.img

Preparamos el futuro soporte , un pincho de 32 GB que me regalaron en navidad ,

 

\[caption id="" align="aligncenter" width="66" caption="Pincho de 32GB"\]![Pincho de 32GB](images/pincho_32gb.jpg "Pincho de 32GB")\[/caption\]

eliminamos las particiones y volcamos el fichero imagen con otro dd

sudo dd if=tdk.img of=/dev/sdb

Parece que esta todo  , pero "una aldea de irreductibles galos sobreviven al invasor" y nosotros tenemos una partición de 4 GB en un pincho de 32GB  , lo veo como que desaprovechado  e inútil. Editamos las particiones y la hago crecer hasta los 18GB. Ya tenemos espacio de sobra , podemos iniciar el servidor con el nuevo soporte para el SO y verificar si reconoce el espacio nuevo. Con el sistema de archivos correcto  , la actualización esperemos que se realice correctamente.

 

### El resultado final:

\[caption id="" align="alignnone" width="649" caption="Webmin Proliant"\]![Webmin Proliant](images/webmin_Proliant.png "Webmin Proliant")\[/caption\]

### Fuente :

[Linuxcomandos.blogspot.com.es](https://linuxcomandos.blogspot.com.es/2008/02/comando-dd.html "linuxcomandos.blogspot.com.es")

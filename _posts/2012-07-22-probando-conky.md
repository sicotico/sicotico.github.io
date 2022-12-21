---
layout: post
title: "Probando Conky"
date: "2012-07-22"
categories: linux
---

Con esa canción sonado en televisión de la tómbola da que pensar.Ahora creo que tiene razón  , vaya mal como me afecta el calor y la publicidad , quieren lavarme el cerebro y yo me resisto lo que puedo .

Buscando una interfaz para la gestión unificada de samba veo en las capturas de ejemplo unos gráficos en el escritorio que indican el rendimiento de la máquina  al mas puro estilo [**gDesklets**](https://es.wikipedia.org/wiki/GDesklets "GDesklets"). Voy a escribir un comentario para preguntar veo que la entrada tiene tropecientos y claro las buenas maneras dicen que primero buscar y luego preguntar.  Olé ya están todo preguntado por lo mismo  , la aplicación es [Conky](https://conky.sourceforge.net/ "conky") y el utiliza un theme llamado [**Conky-Lua**](https://gnome-look.org/content/show.php/Conky+lua?content=139024 "Conky-Lua"). Manos a la obra y la buscamos en los repositorios oficiales Ubuntu y bingo está publicada.

apt-get install conky-all

Ahora toca retocarla un poco , es muy fea para el escritorio de Unity.

[![conky_default](images/7573584514_5fdbdc78c6.jpg)](https://www.flickr.com/photos/12949201@N08/7573584514/ "conky_default por sicotico, en Flickr")

El tiempo apremia , es hora de comer y no voy a retocar ficheros de de configuración .... [ConkyWizard](https://code.google.com/p/conkywizard/ "ConkyWizard") , descargar la aplicación para 32 o 64 bits y ejecutarla. Ahora seguimos los pasos para cambiar colores fondos tipos de letras ,etc ....

Lo que nos soluciona esta aplicación en crear una carpeta oculta en nuestra cuenta de usuario y dejar un fichero de configuración con todas las opciones que marcamos desde el wizard. Ahora solo hay que ejecutar el conky con ese fichero

/usr/bin/conky -c /home/sico/.ConkyWizardTheme/ConkyWizardTheme

Así de bonito queda tras el uso del wizard , y solo han sido unos minutos

[![conky_wizard_default](images/7573629310_77ee4714db.jpg)](https://www.flickr.com/photos/12949201@N08/7573629310/ "conky_wizard_default por sicotico, en Flickr") Ya tenemos todo  configurado  pero si leemos bien al final del wizard te pide que ejecutes Conky con el fichero de configuración que acabas de crear en "Aplicaciones al inicio".

- Nombre: el que tu quieras
- comando: `/usr/bin/conky -c /home/sico/.ConkyWizardTheme/ConkyWizardTheme`
- Comentarios: lo que mas te guste

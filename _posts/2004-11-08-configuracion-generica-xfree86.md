---
layout: post
title: "Configuracion Generica XFree86"
date: "2004-11-08"
categories: 
  - "sin-categoria"
---

### [](https://sicotico.blogspot.com/2004/11/configuracion-generica-xfree86.html)

Para situarnos ahora veremos un sistema nuevo , solo para los que viene de windows , de como funciona las ventanas y como están distribuidas.

Lo primero es la estructura , tenemos un sistema base cuyo interface es una consola , interprete de comandos, después tenemos un servidor de X , que no es mas que un programa que se ha externalizado y es el que controla el hardware ,por tanto si hay que configurar una gráfica tendremos que modificar valores del servidor . Después tenemos los entornos gráficos , las ventanas , KDE y GNOME son los mas importantes y cada uno responde auna filosofía de uso y formas . Estos no son los único también existen los de bajo peso , una de las maravillas de S.O. Linux es poder usar ventanas que usen pocos recursos , para dejarlos libres y que la verdadera potencia del pc sea usada en nuestras actividades . volviendo a nuestros cauces el seleccionar un entorno es trivial los mas importantes son también los mas completos y los mas fáciles de usar , su configuración es trivial ( tipo windows) .

Ahora vamos a lo verdaderamente importante , el Servidor de X "XFree86" , es una herramienta anexa al sistema operativo , desarrollada aparte y como tal en todas sus formas , independiente de la distribución ( Debian , Slackl , Fedora , RedHat , Mandrake ... ) siempre tiene su programa de configuración , aun que podamos tener uno diseñado por las distro también para hacer lo mismo ,por esto denomine Configuración Genérica, ahora los nombres de esto programas son xfree86config viejo donde los aya es una herramienta para configurar las x en las que no necesita arrancar x , por tanto ser haciéndonos preguntas se hará la configuración . La segunda herramienta es xfree86cfg este es mas molón , tiene una interfaz gráfica cojonuda (para los que vengan de windows nop) donde podemos ver todo nuestro servidor x . Aquí hay que tener cuidado es fácil de usar , en lineas generales hay que añadir un grafica , si la hay modificamos sus configuraciones , que son solo bus , que lo optenemso del comando lspci en otra consola y el driver que usa , hay una lista grande donde tenemos que seleccionarlo . Después de la gráfica podemos modificar también la disposición del teclado que a veces esta en ingles y es un coñazo , también deberemos añadir ratones , esto es un truco muy bueno ya que no se sobreponer las configuraciones y si tienes un portátil lo mejor es tener los dos siempre activos , el como es añadiendo dos ratones cada uno con su protocolo , usb y ps2 .

Después de todo esto hay que guardar las configuraciones , la ruta normal es /etc/X11/ , las rutas depende de la distro , pero si no las encuentra en su sitio predefino siempre pasa por esta carpeta , pero si las encuentra por mucho k modifiquemos esta carpeta no nos va a servir de mucho .

Ya hemos acabado tenemos un Servidor X funcionando , siempre que sepamos el driver que necesitamos , su bus , y no cambiemos las cosas al "tuntun" ( en eso yo soy un profesional )

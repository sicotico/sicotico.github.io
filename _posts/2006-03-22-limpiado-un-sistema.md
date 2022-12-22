---
layout: posts
title: "Limpiado un sistema"
date: "2006-03-22"
categories: linux
---

Por si alguien no lo sabia aparte de esas "mi...." de progrmas de windows que te acelran el equipo y te limpia de archivos el sistema y que tan necesario son si quieres que todo vaya perfecto , pues en linux tenemos otro parecido para cuando pasa de version en distro mu veriable socmo fedora o ubuntu , en esta ultima lo he probado yo y funcioan realmente bien.

El progrma se llama **deborphan** y simplemente se encarga de buscar librerias huérfanas. Se mostrará un listado de paquetes que posiblemente no fueron desinstalados en su momento y que actualmente **no** son utiles ni necesarios para el sistema , he visto por internet varias formas de usaro pero todos usan este programa.em pazamos por a instalación y lo hare estilo debian

como root: #apt-get install **deborphan**

Para ejecutarlo hemso de hacerlo con uan tuberia o pipe ya que solo localiza paquetes no necesarios , asi que lo redireccionaremos a un desistalador de paquetes , y como estamso en debian usaremso dpkg o apt-get el que mas rabia os de.

#deborphan | sudo xargs apt-get remove -y

o

#deborphan | sudo xargs dpkg -purge

Con esto ya tendriamso el sistema limpio de libreria inutiles. Si encuentro alguan otra forma de ejecutarlo  lo actualizare , pero como  adelante no e smas que uan tubería y podremso desistalar hasta con yum si se diera el caso.

---
layout: posts
title: "Rutas personalizadas en Ubuntu"
date: "2012-10-16"
categories: linux
---

![menu-lugares](images/7921894824_a0d749b7bd.jpg)

La moda creciente en los sistemas operativos en controlar lo que haces. Como controlar es algo peligroso y no suele gustar la expresión utilizan métodos sutiles.Años de estudios psicológicos dan sus frutos. Debemos de indicar unas carpetas en el disco en las que el usuario siempre tenga un acceso directo. No voy a decir donde han de poner su musica o trabajos del colegio , simplemente coloco accesos directos de forma estratégica para que termine todo allí.

No es solo de Windows Linux también utiliza esta técnica en favor de mejorar la experiencia del usuario. En Ubuntu siempre tienes accesos a descargas, música , etc .. y casualmente en el mismo lugar están en Windows 7. Mis malas experiencia allá por el estreno de windows XP me ha obligado a cambiar siempre la ruta de la carpeta de mis documentos a otra partición para formatear rápido si era preciso.

Hoy toca hacer este cambio en Ubuntu, y con Unity nativo es necesario modificar un fichero , supongo que con herramientas de terceros se puede configurar. Yo soy de la esencia pura y no toco nada , la política  "por defecto siempre va bien".

`gedit ~/.config/user-dirs.dirs`

Con este comando lanzado desde terminal te permitirá modificar las rutas de estos directorios , lo que te encontrarás tiene esta forma:

XDG\_DESKTOP\_DIR="$HOME/Escritorio"
XDG\_DOWNLOAD\_DIR="$HOME/Descargas"
XDG\_TEMPLATES\_DIR="$HOME/Plantillas"
XDG\_PUBLICSHARE\_DIR="$HOME/Público"
XDG\_DOCUMENTS\_DIR="$HOME/Documentos"
XDG\_MUSIC\_DIR="$HOME/Música"
XDG\_VIDEOS\_DIR="$HOME/Vídeos"

Utiliza siempre rutas absolutas o variables del sistema , como se ve en el valor por defecto

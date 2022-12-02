---

title: "Partimage"
date: "2013-07-29"
categories: 
  - "sin-categoria"
---

## El porque de todo esto

He adquirido una vieja gloria de portátil y venia con licencia de Windows XP. Va a tocar actualizarlos , vaya ideas que tengo a veces. Revisamos que tenga el SP3 de rigor y de damos al "Windows Update" , toma ya!!! 250MB en actualizaciones. Esto va a ser un trabajo de chinos.

\[flickr\]https://www.flickr.com/photos/12949201@N08/9373859616/\[/flickr\]

Poco a poco ejecutamos las actualizaciones de windows , _una y otra vez aparecen nuevos parches_. Esto se consigue poniendo de requerimientos un software nuevo , en una versión antigua , y en la siguiente ejecución del Windows Update tendremos más y más.  Solo llevo 1,8 GB de actualizaciones  así que hay que buscar un método de backup.

## El backup

La búsqueda del software tiene como requisito que sea de tipo Ghost.  En OpenSource existe Partimage , ha sido probarlo y enamorarme. Ellos mismo recomienda utilizar el CdSystemRescue como sistema de arranque.

Yo he utilizado un almacenamiento externo para guardar la imagen , para ello he tirado de dmseg tras enchufar el disco externo , obtengo /dev/sdX que corresponde y lo monto en una carpeta dentro de root ,  una costubre.

El sistema de archivos del PinchoUSB es NO-Persisntente !!!! , así que utiliza un disco externo u otra partición en el equipo para no perder lo

### Los pasos

Desde la interfaz de consola ejecutamos el partimage y lo configuramos desde ncurses. Los datos que te piden es la partición o disco que quieres hacer imagen  , la ruta donde guardar el resultado (donde hayas montado el recurso).

 

\[flickr\]https://www.flickr.com/photos/12949201@N08/9371082155\[/flickr\]

La opciones son el nombre , si quieres que se comprima mucho o poco,  usar un servidor de red y decir si se parte en varios volúmenes.

Si no hemos indicado que se cree la imagen en el recurso externo deberemos de copiarla ahora , antes de apagar.

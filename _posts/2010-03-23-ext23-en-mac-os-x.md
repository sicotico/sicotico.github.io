---
layout: posts
title: "Ext2/3 en Mac OS X"
date: "2010-03-23"
categories: mac
---

Lo primero decir que me es imposible usar toda la tecnología de Apple , su sistema de ficheros y todas sus aplicaciones. Espero que no se rompa mucho esto.

En Linux llevan una temporada usando [FUSE](https://fuse.sourceforge.net/) y Google en la MacWorld de 2007 presento MacFUSE. Es un port del proyecto FUSE a la Mac, proporciona una interface para acceder en lectura y escritura a sistemas de ficheros, bloqueados por Apple.

La idea básica es instalar MacFUSE y después una herramienta especifica para cada sistema de ficheros. En este caso usaremos fuse-ext2 , yo utilice el manual de NTFS-3G  y lo adapte a Ext3, este está muy extendido por la red.

1. Descargamos la ultima versión de  MacFUSE en binarios  (MacFUSE-2.0.3,2.dmg) de la web del proyecto : [https://macfuse.googlecode.com/](https://macfuse.googlecode.com/).
2. Montar el MacFUSE-2.0.3,2.dmg en su volumen e instalar el paquete MacFUSE  , viene con instalador  (MacFUSE.pkg).[  
    ](https://4.bp.blogspot.com/_lnQEFwRFpkA/Si08_7YVcsI/AAAAAAAACZ8/-IKyX6DLh1M/s1600-h/MacFUSE+Package.png)
3. Ahora descargamos el binario del  [Fuse-ext2](https://alperakcan.org/?open=projects&project=fuse-ext2) (fuse-ext2-0.0.5.dmg) de la web del proyecto: [https://sourceforge.net/projects/fuse-ext2/](https://sourceforge.net/projects/fuse-ext2/).
4. También lo montamos  y lo instalamos con el instalador propio que tiene the fuse-ext2-0.0.5.dmg
5. Ahora tenemos los módulos instalados conectemos el disco externo con particiones ext
6. Ahora al más viejo estilo Linux tenemos que localizar su dirección de dispositivo de bloques.Para ello utilizaremos la herramienta "Utilidad de Disco" que esta en la carpeta de utilidades dentro de aplicaciones . En la columna de la izquierda  deberías de ver los discos duros , sus nombre  y sus particiones.
7. En nuestro caso montamos disk2s2
8. Necesitamos el Terminal hacer esto, lo podemos encontrar en Aplicaciones.
9. Desde el terminal creamos una carpeta , en /Volumenes/ ,  con el nombre que queramos . Este va ser el punto de montaje . Ahora vamos lanzar el fuse-ext2 para montar el disco con escritura. el primer parámetro son las opciones de montaje , el segundo  es la dirección de nuestro disco y el tercero el punto de montaje.
    
    mkdir /Volumes/myextdrive  
    sudo fuse-ext2 -rw /dev/disk2s1 /Volumes/myextdrive
    
10. [![](images/Terminal.png)](https://2.bp.blogspot.com/_lnQEFwRFpkA/Si1bBvDUBII/AAAAAAAACaU/dJhUQEzNxns/s1600-h/Terminal.png)
11. Felicidades! ya tienes tu disco visible en Finder.[![](images/Finder.png)](https://2.bp.blogspot.com/_lnQEFwRFpkA/Si1baj9At8I/AAAAAAAACac/9UTbusLRGk4/s1600-h/Finder.png)

Actualizado: Para poder montar con permisos de lectura y escritura el volumen desde los menus de Mac OS X debemos modificar el script de montaje y ponerles más permisos Si modificamos el fichero `/System/Library/Filesystems/fuse-ext2.fs/fuse-ext2.util` En la linea : `OPTIONS="auto_xattr,defer_permissions"` Añadimos `rw+` dejando como resultado final: `OPTIONS="auto_xattr,defer_permissions,rw+"`

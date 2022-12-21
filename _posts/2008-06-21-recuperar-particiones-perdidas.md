---
layout: post
title: "Recuperar Particiones Perdidas"
date: "2008-06-21"
categories: linux
---

Buenas , hace mucho que no escribía y claro era por algo importante , el trabajo y los estudios. Así que nos ponemos manos a la obra con un contenido que para mi ha sido importante.

Hace poco perdí 30GB de información en mi disco duro externo y claro eso hay que recuperar lo si o si.El caso fue el siguiente , lo tenia enchufado a un pc para recuperar unos datos y de repente desaparecieron las particiones de mi disco.Eso me pasa por usar el Hiren'sCD en vez de uno en software libre como SystemRecueCD. Asi que explicare como recuperar ficheros sueltos y particiones perdidas cuando ni si quiera el software propietario como Partition Magic o Acronis fueron capaces.

En el caso que nos ocupa no tenemos porque iniciar la maquina con un cd-Live ya que hablamos de un disco externo. Si lo necesitáramos porque es el disco fijo de un pc lo mejor seria descargar el SystemRecueCD y ejecutar el testdisk

`#testdisk`

Puesto que es externo la forma más fácil de actuar es descargarte el programa tanto si es Linux como Windows lo puedes obtener de la pagina oficial. Si tienes Ubuntu tienes que tener activos los repositorios Universe

[Enlace](https://ftp.cz.debian.org/debian/pool/main/t/testdisk/testdisk_6.5-1_386.deb) para Debian

[Enlace](https://ftp.cz.debian.org/debian/pool/main/t/testdisk/testdisk_6.5-1_amd64.deb) para Debian64

[Enlace](https://ubuntu-hr.org/ubuntu/pool/universe/t/testdisk/testdisk_6.8-1_i386.deb) para Ubuntu

[Enlace](https://ubuntu-hr.org/ubuntu/pool/universe/t/testdisk/testdisk_6.8-1_amd64.deb) para Ubuntu64

[Enlace](https://www.cgsecurity.org/wiki/TestDisk_Descargar) a la Pagina Oficial de descargas

**Localizar Particiones**

1. Arrancamos la maquina con el SystemRescueCD
2. Lanzamos el comando "testdisk"
3. No creamos Log
4. Seleccionamos el disco donde buscaremos las particiones
5. El tipo de partición que tuviera el disco
6. Buscamos particiones anteriores (búsqueda poco profunda)
7. Seleccionamos la partición que creemos que es la nuestra
\[Si no esta procedemos hacer un "búsqueda profunda"\]

**Copiar Ficheros sueltos**10. presionando la letra "p" podemos acceder al contenido del disco
11. con la letra "c" podemos copiar ficheros a nuestro disco , al directorio donde estamos
**Recuperar Particiones**13. El programa le dará una lista de las particiones encontradas (en letra gris y con una "D" al inicio) le dirá si es NTFS, FAT, o Linux.
14. Con las flechas arriba/abajo no situamos en la partición deseada
15. Con las flechas izquierda/derecha elegimos la letra del principio de la linea. Estamos indicando tipo de partición es, Extendida, Logica, Primaria, Primaria Booteable. Cuando se ponga en VERDE la linea hemos acertado
16. Ahora saldremos y guardaremos los cambios
17. Reinicie o desmonte su dispositivo o máquina.

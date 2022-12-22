---
layout: posts
title: "Tarjeta de Sonido HDA intel"
date: "2006-03-27"
categories: hardware
---

Bueno he leído muchos problemas sobre estas tarjeta como que usan un modulo raro llamado "snd-xnz" , nada mas lejos de la realidad es un timo , seamos serios , acudamos a la fuente de la información y la tendremos un su estadio mas puro www.alsa-project.org .

 

Magia a parece soportada , según mi lspci tengo un tarjeta

"Intel Corporation 821801/FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)"

 Esto es lo que pone la pagina de alsa:

<table border="1" cellpadding="2" cellspacing="3" width="100%"><colgroup><col width="150*"> <col width="34*"> <col width="72*"></colgroup><tbody><tr><td width="59%">ICH southbridge HD-audio and modem</td><td width="13%">ICH6 ICH6M ICH7 ESB2</td><td width="28%"><p align="center">Details (<a href="https://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&amp;card=ICH+southbridge+HD-audio+and+modem.&amp;chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&amp;module=hda-intel">hda-intel</a>)</p></td></tr></tbody></table>

 

 Por si alguien no lo entiende HD-audio significa High Definition audio , ala que coincidencia ,  tenemos driver y porque no tenemos sonido ?¿?¿?¿??¿.

 

Parte de Diagnostico tipo Cojo de HOUSE .....

Síntomas tenemos un driver para nuestra tarjeta ,así que esta debiera funcionar , pero no lo hace , tenemos alsa ?¿.

 \*Para informático de vocación...... 

Alsa es nuestra herramienta para usar tarjetas de sonido en general , una hardware Layer , pero como soy castellano hablante , seria un capa de hardware . Funcionamiento maneja hardware y hace que un programa de sonido pueda funcionar exclusivamente usado funciones de alsa  , se solía usar como un paquete adicional con un demonio etc , peor en la actualidad esta incorporado en le kernel de todas las distros actuales , así que con un depmod -a seria suficiente para que revisara los módulos y cargara el que necesitámos como hace para el ide , pci , puerto serie etc ...

 

Comprobemos que  tenemos el modulo cargado.

#lsmod | grep snd\_hda\_intel

con que nos aparezca un par de lineas ya valdría para detectar que esta cargado.

Entonces "Diagnostico diferencia" tengo alsa porque esta nativo en el kernel , tengo el driver por la misma razón , esta cargado entonces "depmod -a"  ha realizado correctamente su función , si todo esta bien porque no funciona , bueno pues la repsuesta esta en el modulo es genérico para todas las HD-audio pero hay varias revisiones (rev 04)  entonces para que el modulo funcione correctamente hemos de pasarle un parámetro , un valor que necesita para poder usar esta vesion de tarjeta incluso algunas de (rev 03) , esto se realiza mediante un

#echo options snd\_intel\_hda=5stack >> /etc/modprobe.d/options

 

Reiniciando el sistema ya tenemos tarjeta de sonido funcionado y la mía va de lujo.

Portatil Fujitso Siemens  6453G Pentium M 750 1,87GGGhz FSB 533 , 1GB de RAM DDR2 533 , 80GGGB , ATI X600 de 128MMMB ,DVDRW-DL Dual 8x , TFT 14.1"  

 

Para los que quieren saber mas , modprobe es una herramienta conocida para cargar módulos a mano del kernel pero como el kernel necesita cargar módulos por si mismo en arranque así que se aprovecha de esta herramienta a través de las configuraciones que introduzcamos en /etc/modprobe.d entre ella lo que hemos hecho ahora de dar parámetros a un modulo del kernel  .

 

Hombrecillos pasarlo bien y que os suene mucho la tarjeta de sonido ...............

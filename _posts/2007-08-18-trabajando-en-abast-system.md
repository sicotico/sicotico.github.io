---
layout: post
title: "Trabajando en Abast System"
date: "2007-08-18"
categories: 
  - "sin-categoria"
---

Hace un par de semanas que no escribo nada , bueno tengo una escusa , o mejor dicho dos , he empezado a trabajar y hay que estudiar para septiembre.

He empezado un nuevo portal basado en Drupal con un amigo y esperamos que se unan más.

Para "des-stresarme" me he instalado una Debian Lenny/Sid netinstall con sistema base , en mi Dell 1501 .  Lo primero que he de decir es que la wifi Broadcom 43xx no funciona ni con NidisWrapper ni con el modulo bcm43xx , tal como vienen empaquetados con kenel que no sean el de instalación un 2.6.18 .

Primero Ndiswrapper no se puede usar con esta tarjeta con una versión de Kernel superior a 2.6.20 , en caso de Debian todo esta por encima.El caso es que en la evolución del kernel de ha cambiado el ultimo parámetro de una función a NUL  \[estoy intentado recupera la dichosa página en al que lo leí\] .

Para el el caso del bcm43xx no utiliza correctamente el firmware , carga el dispositivo pero haciendo un iwconfig te responde diciendo que solo se puede hacer con kernel versión 20  y no 22 como tengo yo instalada.

Según se instalar hay que retocar el /etc/bashrc para activar los colores , y algo que he hecho es desactivado del sonido horrible de la consola.

(el script de quitar sonidos)

Yo instale desde el primer DVD restingiendo a sistema base y Laptop . Así que para los repositorios he usado la herramienta "netselct-apt -s -n -f" genera un fichero sources.list en la ruta donde se ejecuto

Por ahora el problema que he tenido ha sido la wifi Broadcom renombrada como "Dell Wireless 1390".

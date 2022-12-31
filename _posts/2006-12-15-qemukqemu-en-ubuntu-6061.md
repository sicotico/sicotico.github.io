---
layout: single
title: "QEMU+KQEMU en Ubuntu 6.0.6.1"
date: "2006-12-15"
categories: vmware
---

Bueno en su día intente qemu y me casco instalado un winxp , si es que es malo hasta par a maquinas virtuales , nadie lo ha confirmado pero siemrpe lees "se me peta la instalación de winxpSP2" y otro dice  "a mi también pero probé uno con SP2 y funciono". Como esto lo lei ahora y no cuando lo intente yo , pues me desilusione. Mientras tanto como una mosca cojonera andaba mi  amigo Diego diciendo "yo la uso en mac y la usaba en Debian y va de lujo" . Así que con la moda de vmware tras la liberar vmware-player , vmware server y vmware-tools he decidió volverlo a intentar.

Tras googlear un poco un amable blogero [LinuxMan](https://linuxman.blogsome.com/) dio la fuente de su post , cosa que hacen pocos ,  ([Installing QEMU, KQEMU, and DHCP Patch](https://www.ubuntuforums.org/showthread.php?t=187413)). Pues bien un maravilloso script que te baja los sources y te los compila y empaqueta . Los fallos que me dio fuel el no poder recuperar el \*.deb porque tras instalarlo lo borra todo . También hay que leer bien las primeras lineas porque si intentas instalar el parche **Mouse Wall Bug Patch** te da error y casca , normal si hubieras leído especifica que solo para versiones menores de 0.8.2 casualmente en la que estamos.

Personalmente me modifique el script para que no borrara nada y así obtener el paquete deb. El cual no se puede distribuir porque el Kqemu tiene licencia no GPL, pero que me he guardo para futuras ocasiones personales.

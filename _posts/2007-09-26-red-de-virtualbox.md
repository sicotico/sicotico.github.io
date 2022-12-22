---
layout: posts
title: "Red de Virtualbox"
date: "2007-09-26"
categories: vmware
---

Teniendo varias maquinas virtuales podemos unirlas en una red. Solo necesitamos que se les asignen ip de nuestra red , no esas de tipo [10.0.2.15](https://10.0.2.15/) .

Para ello tenemos que crea "virtual interface host" , en la configuración de la red : Configuración - Red - boton pequeño a la derecha

Ahora por cada maquina virtual necesitamos un nuevo interface y se creara uno en nuestro host. A cada maquina virtual la configuramos con "interface de anfitrio" por supuesto distintos entre ellos. En este punto tenemos varioas tarjetar de red en nuestro ordenador y necesitamos que todas obtengan ip de la misma red.

Esto lo solucionamos creando una conexion puente y añadiendo a ella la tarjeta de red fisica y las virtuales.

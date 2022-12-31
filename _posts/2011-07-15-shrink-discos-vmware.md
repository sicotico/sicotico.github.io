---
layout: single
title: "Shrink discos VMWare"
date: "2011-07-15"
categories: vmware
---

Cuando trabajamos con maquinas virtuales con software de escritorio tenemos la posibilidad de utilizar discos con crecimiento bajo demanda. Esto puede esta muy bien porque de forma automática crece según lo necesitemos , hasta el limite marcado. Yo uso mucho esta utilidad en trabajo , instalando software y cuando desinstalas el fichero no reduce su tamaño en disco , esto no es automático , una pena. Este proceso tiene un nombre Shrink , analiza el disco y reduce su tamaño en disco. Tener en cuenta que este proceso depende enteramente de la velocidad del disco y se puede demorar bastante.

¿Como hacerlo? En VMWare player necesitamos arrancar la maquina virtual y tener instaladas la vmware-tools , algo que seguro esta instalado ya que mejora bastante el rendimiento.Tenemos la opción de "shrink" e indica sobre que unidades podemos y sobre cuales no.

---
layout: post
title: "Servicos usando services"
date: "2012-02-02"
categories: linux
---

Mejorando el uso elegante y con estilo de sistemas sin entorno gráfico utilizamos el reinicio de servicios para aplicar cambios y para toda esa infinidad de pruebas que nos iluminan a hora intempestivas de la noche.

Desde no se que versión tenemos la herramienta `service` . Con esto nos facilita el acceso a las ruta `/etc/init.d` tan mítica

El parámetro base con el que verificaremos el estado es `--status-all` .Con el veremos el estado de los servicios , indicado mediante un **+/-** si esta iniciado o no

**Ejemplo**

- service --status-all
- service idmapd start
- service idmapd stop
- service idmapd restart

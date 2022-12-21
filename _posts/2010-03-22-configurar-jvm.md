---
layout: post
title: "Configurar JVM"
date: "2010-03-22"
categories: dev
---

Buenas hoy toca librarse del típico error :

### java.lang._OutOfMemoryError_: _Java_ heap space

Si tenemos una aplicación corporativa con una maquina virtual de java propia  o de sistema y te escupe  el error de memoria. Solo tenemso que buscar el jvm.cfg asociado a nuestra java virtual machine y listo.

<instalación de Java>jre6libi386jvm.cfg

\-Xmx 3072 -Xms 1536

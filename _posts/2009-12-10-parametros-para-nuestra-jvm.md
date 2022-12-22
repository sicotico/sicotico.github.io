---
layout: posts
title: "Parametros para nuestra JVM"
date: "2009-12-10"
categories: dev
---

Como Consultor de productos OpenView siempre estoy ligado con aplicativo hechos en java. Esto quiere decir que necesitan mucha memoria y no por defecto el sistema operativo no se la da.

Siempre que se pueda , esto es relativo, podemos buscar la JVM dentro de la carpeta del propio software. Si no existe deberemos ir a la de sistema y asignar los valores de tamaño máximo y mínimo de ram que deseamos que aproveche nuestro Java.

Los paramentos de la JVM son :

\-Xms

Por ejemplo: `-Xms6291456, -Xms6144k, -Xms1500M`

\-Xmx

Por ejemplo, `-Xmx83886080, -Xmx81920k, -Xmx1500M`

El error típico que suele parecer es: `Java Heap Space`

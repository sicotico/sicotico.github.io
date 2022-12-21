---
layout: post
title: "Apagado y reinicio programado en Linux"
date: "2010-12-09"
categories: linux
---

**De acción inmediata:**

- apagar: **sudo shutdown -h now**
- reiniciar: **sudo shutdown -r now**

**Especificando una cantidad de minutos:**

- apagar: **sudo shutdown -h <tiempo>**
- reiniciar: **sudo shutdown -r 30**

**Especificando una hora determinada:**

- apagar: **sudo shutdown -h <hora determinada>**
- reiniciar: **sudo shutdown -r <hora determinada>**

Para cancelar el reinicio o apagado : **sudo shutdown -c**

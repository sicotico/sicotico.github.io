---
layout: post
title: "Aplicaciones por defecto en KDE"
date: "2006-10-26"
categories: 
  - "sin-categoria"
---

Para modificar esas aplicaciones que KDE nos carga con las suyas predeterminadas , como son el ktorrent , kcontac , o basicamente cualquier programa que empiece por k.........

Podemos evitarlo en mayor o menor medida , desde el "Preferencias del Sistema" o "Centro de Control" , componentes de KDE y seccionde aplicaciones , desde ahi podemos modificar algunas.

La que a mi mas me interesaba era evitar Konquero para web y usar Firefox asi , con [esta](https://www.mozilla.org/unix/remote.html) guia de mozilla nos da la linea exacta con la que encima nos abriria pestañas en un firefox abierto.

firefox -remote "openurl(%U,new-tab)" || firefox

Si eres delos que no les gustan las pestañas la linea seria

firefox

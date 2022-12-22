---
layout: posts
title: "Hoy toca un poco de cut"
date: "2011-02-24"
categories: linux
---

El comando cut realiza cortes verticales , sobre unos datos ya sean un fichero o una re dirección .

Selecionar:

- una columna (por defecto usa tab)
    - `cut -f 1`
- un carcater  (posicion 2) 
    - `cut -c2`
- caracteres suelstos
    - `cut -c2,4,7,9`
- intervalo de caracteres
    - `cut -c1-8`

---

title: "Como hacer port forwarding a través de un tunel ssh"
date: "2011-09-10"
categories: 
  - "sin-categoria"
---

Redirigimos un puerto "puerto1" en la "maquina1" a otro puerto "puerto2" en la "maquina2":  
  
user@maquina1$ **ssh user@maquina2 -L puerto1:maquina2:puerto2 -g**  
  
Ahora el puerto "puerto2" de la maquina "maquina2" es accesible por medio del puerto "puerto1" de la maquina "maquina1".

![](https://blogger.googleusercontent.com/tracker/3262098284547378612-3318900979857819167?l=tablondesastre.blogspot.com)

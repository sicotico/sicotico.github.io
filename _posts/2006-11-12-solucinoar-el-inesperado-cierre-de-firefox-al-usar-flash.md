---

title: "Solucinoar el Inesperado cierre de Firefox al usar Flash"
date: "2006-11-12"
categories: 
  - "sin-categoria"
---

Por ahora es uno de los fallos que he conocido en mis propias carnes .Actualemnte me han habaldo de otro por javascript , pero como uso [NoScript](https://www.noscript.net/ "https://www.noscript.net/") no me ha ocurrido .

Esta solucion es de Ubunut-es.org y por ahora parece que funciona , aunque espero que saquen una solucion propia la [Fundación Mozilla](https://www.mozilla.org):

1) Editar el fichero /etc/firefox/firefoxrc y poner: export XLIB\_SKIP\_ARGB\_VISUALS=1

2) Editar el fichero /etc/X11/xorg.conf : En la sección Screen, cambiar DefaultDepth a 24 bits.

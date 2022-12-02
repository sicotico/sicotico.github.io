---

title: "Borrar disco duro"
date: "2009-12-26"
categories: 
  - "sin-categoria"
---

Como ya había comentado , se me peto un disco duro y como no me fío mucho he indagado un poco sobre los formateos a bajo nivel en linux. En windows es muy fácil coger la herramienta del fabricante , si la tiene y no era mi caso , Treckstor no tiene muchas cosas más que un precio reducido.

No voy a decir que n linux en más facil porque hay que buscar el comando y sus parámetros , pero cuando menos no tengo que instalar nada **¡viva dd!**.

`sudo dd if=/dev/zero of=/dev/ bs=1M`

El tiempo que me consumió para un disco de 500GB fue de 16 horas. Tras esto no queda MBR , tabla de particiones ni nada , así que no os asustéis si no se os vuelve a montar el disco , tenemos un [manual](https://manual.sidux.com/es/part-gparted-es.htm) de gparte que explica como crear particiones

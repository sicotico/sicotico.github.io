---
layout: post
title: "Resetear password Deluge web"
date: "2010-03-23"
categories: software
---

Es un cliente de torrente un poco complicado , pero muy versátil , todo se paga en esta vida.

Para cambiar la pasword del modo web hemos de realizar estas tareas:

- Parar el deluged y deluge web , los procesos son:
    - deluged y deluge -ui web
- Borrar el fichero
    - `~/.config/deluge/webui06.conf.new`
- Iniciamos el demonio "deluged"
- Iniciamos el interfaz web
    - deluge -ui web
- La password por defecto es "deluge"

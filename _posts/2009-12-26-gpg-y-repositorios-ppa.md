---
layout: posts
title: "GPG y repositorios PPA"
date: "2009-12-26"
categories: dev
---

Instalando el NUV me daba un error de GPG para repositorios de tipo PPA , la solución pas apor conocer el servidor de claves de ubuntu `keys.ubuntu.com`

El error mostrado:

`W: Error de GPG: https://ppa.launchpad.net jaunty Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 5D49322B623C928A`

Un modo más rápido es:

Paso 1. `gpg --keyserver keys.ubuntu.com --recv-keys "vuestra KEY"`

Paso 2. `gpg --export --armor "vuestra KEY" | sudo apt-key add -`

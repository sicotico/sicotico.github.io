---
layout: single
title: "Mejoras Firefox"
date: "2005-08-14"
categories: software
---

Con esto vamos a mejorar el rendimiento del firefox .....

En Firefox abrimos la dirección "about:config" (Sin las comillas), y en este lugar modificaremos los siguientes valores

Cita: browser.turbo.enabled true

network.http.pipelining true

network.http.pipelining.maxrequests 8

network.http.max-connections 30

network.http.max-connections-per-server 8

network.http.max-persistent-connections-per-server 8

nglayout.initialpaint.delay 100

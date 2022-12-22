---
layout: posts
title: "Información de Vistas en Oracle"
date: "2009-11-16"
categories: software
---

Me ha tocado un Oracle y hacerme un hombre con la consola , que forma más bonita de explicarlo.

Primera petición y en la frente. Para descubrir las consultas asociadas a una vista en Oracle y no tenemos ninguna herramienta gráfica a mano.

`set long 4000` `select text from user_views where view_name = 'nombre de la vista (con las comillas)'`

Importante decir que esta información salio de la cabeza J.A

---
layout: post
title: Hostinger y GitPages
subtitle: 
tags: [jekyll]
comments: false
---

## __Sprint 1__  
  
Me falla el dominio tras cancelar el hosting de WP, valido el dominio y GitPages lo muestra correcto

## __Sprint 2__

https://dev.to/sidmohanty11/how-to-add-a-custom-domain-to-github-pages-hostinger-edition-p4p

https://dev.to/bkanhu/auto-deployment-of-website-with-github-and-hostinger-563p

## __Sprint 3__

Tras superar las vacuna del más pequeño de mi niños, he sacado un rato para terminar y valido el subdominio github y la web. Funciona correctamente. Pero el dominio ed luispuente.net está peleón.

Organizo tareas, aver que resultados me encuentro
- Reviso que via móvil hostinger funciona
- Git-Pages tiene verificado el dominio
- pero no funciona
- el subdominio de github va correctamente

A día de hoy  mantengo el entorno local de Ruby y Jekyll, solo borré el contenido y cree el fork el tema que me gustaba.

Por ahora escribo este artículo para poder recordad como hice funcionar y como hostinger me da errores muy extraños.Tengo las DNS de IBM configuradas en el router y me falla el acceso a hostinger. Este es el error que me da:
~~~
hunkLoadError: Loading chunk 242 failed.
(error: https://js-agent.newrelic.com/session-manager.2a8d47d1-1.232.0.min.js)
    j https://www.hostinger.es/cpanel-login:1
    e https://www.hostinger.es/cpanel-login:1
    e https://www.hostinger.es/cpanel-login:1
    e https://www.hostinger.es/cpanel-login:1
    importAggregator https://www.hostinger.es/cpanel-login:1
~~~

Los navegadores locales se vuelven locos redirigiendo a la home una y otra vez.

Accedo via datos móviles y funciona correctamente, valido con una sesión privada de Firefox y accedo al panel. Terminaré migrando el domino a otro registrados con un portal algo mejor. Antes lo tenia con la promo de 48 meses, era realmente barato  pero ahora, el gratis de Git-Pages tiene su encanto y sin base de datos aún más.






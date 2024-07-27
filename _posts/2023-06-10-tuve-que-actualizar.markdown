---
layout: post
title: Cambio de plantilla
subtitle: 
tags: [jekyll]
comments: false
---



## __Sprint 1__  
  
Veo errores en mi local e Jekyll y no genera el contenido estático. Entro en pánico, ya no me acuerdo como funciona esto, y por esto me refiero a Ruby en windows  pero bueno tengo un post en el que lo explica pero al leerlo no me convences. ¿Vuelvo a montar esto  o hay alguna forma mejor de vivir?

Pues sí la había, otro tema con unas instrucciones de tres paso , que bien podía haberlo hecho la primera vez. Si, usando el editor de github podía haber modificado las plantillas y subido los post de una forma sencilla. Todo web y sin ensuciar el equipo , también podia haber elegido HUGO y espero Go si fuera más amigable con windows. Pero bueno  que me voy por la ramas.

He buscado otra forma de hacerlo, simplificando mi flujo de trabajo. 

- fork del tema
- modificación desde web del _config.yalm
- Y el action automático

## __Sprint 2__

El tema elegido [beautifuljekyll.com](https://beautifuljekyll.com) , con el modo de 3 paso , la verdad es que no miré las características. Seguí los pasos y lo tenía desplegado, 

- Borro renombro el repositorio web y genero uno nuevo
- hago un fork del nuevo tema
- Modifico lo básico via web de github

Pero no me funcionaba, algo se ha desconfigurado en el dominio. Evalué que podia terminar y no lo ví nada claro, ale a dormir. 

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






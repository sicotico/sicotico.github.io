---
layout: post
title:  "Prototipo de App estática en Azure"
date:   2023-05-20 10:57:08 +0200
tags: [azure,StaticWebApp]
---

  
# La idea es crear una aplicación en Azure sin servidor. 

## __Sprint 1__  
  
Formarme un poco en las ultimas tecnologías web. Vengo de WordPress y aquí he decidido hacerlo ligero , craso error. El mundo de las SPA  , React, Angular , ... me ha adelantado por la derecha.

Perdí mucho el tiempo viendo videos y comparativas. Repase muchos conceptos de JS que tenía olvidados  y luego rebusque por lo servicios de Azure  cual es el que menos desarrollo necesitaría para mi idea.

El servicio elegido fue Azure Static Web App, apoyándome en Js podría crear un web sin base de datos ni back-end.

Asi que toco trabajar algo:

- Repo en git
- Servicio de Azure Static Web App, 
- Ejemplo del luna app vanilla corriendo en el servicio
- Ejemplo de app con autenticación, sin mucho glamour, clone uno de Git pero no me funcionó

Lo primero fue crear un Static Web App con el artículo [Inicio rápido: Creación de la primera aplicación web estática](https://learn.microsoft.com/es-es/azure/static-web-apps/get-started-portal?tabs=vanilla-javascript&pivots=github), con esta guía cubrí todos los pasos


## __Sprint 2__

Asi que toco trabajar algo:

- Repo en git
- Servicio de Azure Static Web App, 
- Borrado de la app vanilla
- Despliegue de las apps de ejemplo en Angular ¡
- Ejemplo de app con autenticación, sin mucho glamour, clone uno de Git pero no me funcionó

Como ya tenia la app desplegada en vanilla, la borre y la generé con Angula y con VUE, si lo hice varias veces. Al arrancar el servidor local de pruebas todos los desarrollos daban error de OpenSSL. Al buscar solo me decía que actualizara NODE y Angular, no tenia sentido ya que estaban recién instalados. En uno de los artículos indicaba que utilizar aversiones viejas porque le Angular que se utilizó para los ejemplos era demasiado antiguo. Obviamente no podemos poner librerías tan antiguas en internet. Busque otro ejemplo, un momento de iluminación me llevo a la web de Angular y utilizar su [app de ejemplo](https://angular.io/guide/example-apps-list), lo probé y funcionó .


Ejemplo pero busqué un poco y encontré este [repo](https://github.com/azure365pro/AzureAD-StaticWebApp-LoginPage) donde ya estaban la rutas básicas y el iDp configurado. Es un poco de trampa porque te saltas muchos conceptos de rutas y configuraciones básicas del fichero _staticwebapp.config.json_

Hablo con conocimiento de causa, tuve que revisar la documentación después

Aquí jugamos con el fichero de configuración para utilizar Azure AD [Autenticación y autorización de Static Web Apps](https://learn.microsoft.com/es-es/azure/static-web-apps/authentication-authorization) 

Ahora y si estamos autenticados podemos consultar la [información que nos proporciona el IDP](https://learn.microsoft.com/es-es/azure/static-web-apps/user-information?tabs=javascript) 


## __Sprint 3__

Se supone que los años de arquitecto me han generado un poco de toc, asi que lo primero sería empezar por la arquitectura de la aplicación. Pero va a ser que no. Ya llevo cosas hechas y valorando diferentes opciones, asi que el enfoque que he llevado es más de RAD. Cuando tienes bastantes ideas claras, estas son las que tengo yo ahora:
- La idea principal
- Autenticación
- Funcionalidades básicas

Pudo empezar con la arquitectura, la visión funcional 

![arquitectura](../assets/img/spav1.png)

Empiezo por el principio, primero crear la arquitectura según requisitos. El interesado soy yo así que espero comunicarme bien conmigo mismo. Tras revisar la documentación de arquitectura de azure para aplicaciones sin servidor, es verdad que Serverless queda mucho más molón. Me he inclinado por un SPA. Este es el visio del ejemplo básico.

[![SPA Azure arquitectura](https://learn.microsoft.com/es-es/azure/architecture/reference-architectures/serverless/_images/serverless-web-app.png)](https://learn.microsoft.com/es-es/azure/architecture/reference-architectures/serverless/web-app)

También me he basado en el libro "Diseño de la arquitectura de aplicaciones .NET nativas en la nube para Azure", está descargable y gratuito [aquí](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf)





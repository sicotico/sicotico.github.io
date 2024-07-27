---
layout: post
title:  "Proyecto personal en modo ágil"
date:   2023-01-01 10:57:08 +0200
tags: [jekyll,update]
---

Hay cosas que es mejor no hacer.

Aclaro mejor el entorno donde empecé fue un Windows 10 con vscode y lo uso más para analizar JSON y biceps que para desarrollar. 

Viendo que había compatibilidad en windows pues me tiré a la piscina para terminar lo antes posible. Ya de entrada necesitabas un paquete especial,el Ruby+Devkit, ejecutar ridk y terminales MINGW. Esto no me alerto de la instalación ta sucia que conllevaba.

---
* Ruby y devkit en el raíz
* Las gemas de jekyll y bundler a nivel SO
  
---

__Planteamiento__

Hey que soy Scrum Master y Product Owner, voy a poner en práctica lo que se y mi experiencia par aun proyecto ene l que tenemos la idea pero también una incertidumbre de como llevarlo a cabo. Lo primero es la idea de lo que queremos conseguir  y eso ya está aclarado en otro post. Lo segundo establecer a los interesados, una de mis otras personalidades me hará de interesado.  La parte de un equipo en el que todos los integrantes conozca las tecnologías a utilizar no la voy a cumplir, habrá que incluir en los sprints horas de investigación.

__Sprint 1__  
  
El entorno local lo cree en el post [Aventuras de WordPress a Jekyll](2022-11-02-aventuras-de-WordPress-a-Jekyll.markdown)

__Sprint 2__

En este punto empece con la migración de contenido, extraer los post de WordPress en formato markdown parecía fácil, hay un script para esta tarea. Tuve mala suerte con la gema de mysql y no la detectaba a nivel de SO ni ejecutando un entorno de bundler para la migración. Siempre hay un plan B y en este caso fué un plugin en WordPress !(Jekyll Exporter)[https://wordpress.org/plugins/jekyll-exporter/], con el obtenemos un zip con todos los artículos en fichero markdown separados y listos para incluir en la carpeta "_posts". El problema descrito en 4 lineas me llevo 4 días, es lo qu tiene no tener ni idea del entorno Ruby.

__Sprint 3__  

Con un entorno local funcionado ya nos ponemos manos a la obra con el nuevo blog estático. Según creo el proyecto lo veo funcionado, añadir los post es simplemente crear una carpeta con el contenido el resultado del plugin de WordPress, al crear el proyecto se genera con el tema  _minima_. Que resuena en tu cabeza, ya está casi hecho, a buscar un tema molón como los de WordPress que tiene panel de control y se configuran en nada. Si he escrito esto para que el que lo lea se ria un rato, obviamente no salio el plan así. Haber alma de cántaro, es contenido estático un poco listo, donde va haber un panel de gestión. Primer tema y veo la configuración por ficheros (eso no terminaba nunca), ya no me acuerdo el numero de lineas pero me dio mareos. No puede ser tan difícil editar el tema de _minima_ para dejarlo bonito. Cambio de rumbo. 

__Sprint 4__  

Tema _minima_- Tampoco salio, bueno funcionar funcionaba a veces, como que a veces y si lo subía git se rompía o no se parecía al local. Días leyendo a rato, borrando cache del servidor jekyll , modificando plantillas, probando temas en gema  y en remoto. Ninguna mejora , todos los errores y los fallos del estilo eran aleatorios.

__Sprint 5__  

Borrar y volver a empezar. 
* Borro todos los ficheros (salvo la carpeta post 
* Aplico cambios al git
* Limpio la gemas del sistema
* Genero nuevo bundler 
* Genero proyecto
* Cargo los post 
* Pruebo en local y todo perfecto con el tema básico
* Lo subo a git y perfecto

Ya no lo toco unas semanas para aclárame las ideas

__Sprint 6__  

Nuevo tema 100% compatible con GitPages - Aquí pues que contar, no hay por donde cogerlo. Un tema precioso y con una web super documentado, pero oye que no lo entendía. Unos días mirando a ratos y tiene 3 estructuras completas. La que carga por defecto esta casi vacía, hay una carpeta con lo mismo  mas datos de ejemplo  y otro con  más contenido aun que es la de la doc. Toda una gran novela al estilo del señor de los anillos.

__Sprint 7__  

Vuelta a las modificaciones - Ahora tenia el pecho hinchado, esto lo hago yo en un rato,  pues nada al tajo. Mismo problema los cambios no se ven siempre, el parámetro --incremetal del servidor de jeckyll no funciona y empieza la desesperación. Esta vez con golpe de suerte , cierro el cmd de jekyll y lo vuelvo abrir cargo el server  y veo todos los cambio funcionando. Pues sí el cmd o powerShell de Windows 10 se atasca y no da error con el servidor de Jekyll. He de decir que no lo he solucionado, simplemente he cambiado mi rutina de trabajo y cuando tengo un hueco para el siguiente sprint lo instalaré en el WSL y veré si ahí me funciona mejor. Eso espero, asi puedo eliminar todo el Ruby de mi equipo.


__Sprint 8__ 

Cambiar dominio a Git-Pages, ha sido lo más fácil. Es algo muy simple, la direcciones se basa en un registro CNAME y en una validación.

En el medio he recolocado un poco los archivos, al inicio solo tenia una página  y por si tendría más he creado un carpeta para página, la de los post viene por defecto. Esta carpeta también indica el tipo de contenido, asi que en la configuración lo que incluye realmente son los parámetros de visualización para los tipos.


```yaml
  # _pages
  - scope:
      path: "_pages"
      type: pages
    values:
      layout: single
      author_profile: true
```

Lo malo es que se me olvido migrar mi Tiny Tiny RSS y me he migrado a la app de Inoreader. El servidor ya está vacío y ahora toca generar contenido aquí.


__Sprint 9__

Afinando un poco los detalles he deshabilitado las migas de pan porque no he generado paginas para cada categorías. Las migas de pan te redirigen a una pagina de tipo categoría con todos los post de la misma y yo solo utilizo un general en modo rejilla y siempre redirigía a un página no encontrada. Esto se modifica en el _config.yml con simple true/false. 

Las cosas no salen siempre a la primera, la eliminación de la migas de pan  por la falta de pagina de categorías ha funcionado a la perfección.  Por lo menos técnicamente, al final de cada post se indica las categoría a las que pertenece el post  y son un enlace a esas páginas de categoría que no tengo. Revisamos la documentación del tema para buscar un solución, parece que la página de las categorías es una piedra angular de la navegación.

Es de las pocas veces que la filosofía de menos es más no me ha funcionado. La experiencia del usuario gira en torno al contenido y sobre todo su organización. Esta vez generar el mínimo numero de página solo me ha generado trabajo. Y la solución es extremadamente sencilla.
Este el código de la plantilla para un página de categorías genérica, solo se necesita un archivo de este tipo para que la navegación sea satisfactoria.

category-archive.md

```yaml
---
title: "Posts by Category"
layout: categories
permalink: /categories/
author_profile: true
---
```


Corrigiendo los errores de inicio del servidor de Jekyl. Los error que tenía era que se necesitaba cargar las gemas de wdm y farady, estas tienen una dependencia del sistema operativo y no se cargaban usando :

```ruby
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
```

No detectaba el que corría en plataforma windows y no se cargaban , asi que las cargo siempre

```ruby
source "https://rubygems.org"
gemspec
gem 'faraday-retry'
gem "wdm", ">= 0.1.0"
```


Referencias: 

1. [sintaxis Gemfile](https://tosbourn.com/what-is-the-gemfile/)

---
layout: post
title:  "Aventuras de WordPress a Jekyll"
date:   2022-11-26 10:57:08 +0200
tags: [jekyll]
---

### Contexto

Evaluando los costes de un servidor web y lo poco que miro para el blog he decidido usar un plataforma gratuita, rápida y barata. He llegado a Git-Pages con el motor de Jekyll para migrar mi blog.

En este momento no sabía lo que era Jekyll ni Ruby, pero si que valía para hacer blogs en GitPages. Así que había que leer un poco.

Lo primero es instalar Ruby en windows, para esto utilicé la [web de Jekyll](https://jekyllrb.com/docs/installation/windows/)

Ahora la recomendación es un bundler y tampoco sabía lo que era ni lo que hacía. 

### Lo básico es empezar por el principio  

__Conceptos:__
* Ruby es un interprete
* Sus dependecias se llaman gemas
* Jekyll es una gema, el generado de sitios estáticos usado por Git-Pages
* bundle es una gema, gestor de dependencias

__Pasos generales__
* Instalar
* Ruby , esto dependiente del SO
* Instalar Kekyll
* Instalar bundle

# ¿Que es bundler?  

Es un manejador de dependencias, como estamos en Ruby a partir de ahora usaremos la palabra gema para referirnos a dependencias, básicamente genera un espacio para dependencia por proyecto, así tienes tus dependencias en tu proyecto.  

En el directorio de proyecto ejecutas bundle y se instalar las dependencias definidas en el fichero `Gemfile`

# ¿Que es Jekyll? 
Un motor para convertir texto plano en webs estáticas  o blogs con categorías  , post personalizados.

### Cosas para hacer

## ¿Como se instala Ruby?

Se explica mucho mejor que yo  la documentación oficial [Doc Jekyll - Instalar Ruby en Windows](https://jekyllrb.com/docs/installation/windows/)

# ¿Como se instala una gema ?
Como mencionamos antes, una gema es una dependencia/librería , asi que utilizaremos comando del propio Ruby.

```bash
$ gem install [nombre de la gema]]
```  

Aquí es donde tenemos que tener en cuenta los alcances de estas acciones.
Este comando actúa a nivel de cuenta de SO , asi que todos los proyectos utilizaran las mismas versiones. Esto es problemático si tienes proyectos antiguos que no puedes actualizar las versiones de las gemas que utilizan. 

# ¿Por qué usar bundle?
Para solventar el problema que existe con las dependencias a nivel de SO gema, ___bundle___, con este comando se instalaran las gemas a nivel de carpeta/proyecto. 

___Recomendación:___  
Lo mejor es no instalar gemas a nivel de SO para evitar conflictos con tus proyectos.


Son gemas de Ruby, así que la instalación es con el siguiente método estándar  

```bash
$ gem install bundler jekyll
```  

Situados en el directorio del proyecto, necesitamos crear el fichero `Gemfile` (sin extensión)
Este ha sido generado por mi para el primer intento de migración, utilizo lo mínimo posible, la gema de Jekyll, minima es un tema para github, el más básico y el plugin de jekyll-feed (generar rss), me vine arriba y puse cosas a futuro que aun no he configurado. La gema webrick es requisito si usas Ruby 3 o superior

Mi fichero `Gemfile` quedaría de la siguiente manera:

```ruby
source "https://rubygems.org"

gem "jekyll", "~> 4.2.2"
gem "minima", "~> 2.5"

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
end

platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", "~> 1.2"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
gem "webrick"
```

Como siempre se me olvida, este el comando para levantar un servidor de jekyll en la carpeta donde tengas el contenido

```sh
 bundle exec jekyll serve --incremental
```  

Referencias: 

1. [Doc Jekyll - Instalar Ruby en Windows](https://jekyllrb.com/docs/installation/windows/)
2. [Doc Jekyll - Quickstart Ejecutar un servidor  local de Jekyll](https://jekyllrb.com/docs/)
3. [Doc Jekyll - Posts](https://jekyllrb.com/docs/posts/)
4. Opcional , resolver problemas con bundle  
4.1. [Instalar Bundler](https://jekyllrb.com/docs/step-by-step/01-setup/)  
4.2. [La documentación de la gema bundler](https://bundler.io/docs.html)  
4.3. [Manejo-de-dependencias-en-ruby-con-bundler)](https://blog.makeitreal.camp/manejo-de-dependencias-en-ruby-con-bundler/)  
5. Método alternativo de tener [Jekyll y bundler](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/)

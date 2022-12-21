---
layout: post
title: "Ubuntu y Python"
date: "2014-03-30"
categories: linux
---

Entrar en consola e instalar: sudo apt-get install python-pip (paquete para instalar modulos de python) sudo pip install -I Django==1.5 (instalar el paquete django) sudo apt-get install apache2 sudo apt-get install mysql-server sudo apt-get install phpmyadmin sudo pip install mysql-python

Error:: [linux mysql-server can't find mysql\_config](https://stackoverflow.com/questions/8496660/linux-mysql-server-cant-find-mysql-config "linux-mysql-server-cant-find-mysql-config")

sudo apt-get install libmysqlclient-dev

Error: [Python.h: No such file or directory](https://stackoverflow.com/questions/11041299/python-h-no-such-file-or-directory "python-h-no-such-file-or-directory") sudo apt-get install python2.7-dev sudo apt-get install python-virtualenv

Para crear proyectos debemos de seguir los siguientes pasos: Pasos en consola linux: virtualenv dj14 ./dj14/bin/pip install django ./dj14/bin/pip install django-registration ./dj14/bin/pip install mysql-python ./dj14/bin/pip install flup ./dj14/bin/pip install django-debug-toolbar ./dj14/bin/pip install South

sudo apt-get install python-setuptools python-dev build-essential python-mysqldb python-tz python-imaging /dj14/bin/pip install pil

sudo apt-get install python-mysqldb

/dj14/bin/python manage.py syncdb ~/dj14/bin/python manage.py migrate

Pasos en consola Windos: virtualenv dj14 .\\dj14\\Scripts\\pip install django .\\dj14\\Scripts\\pip install django-registration .\\dj14\\Scripts\\pip install mysql-python .\\dj14\\Scripts\\pip install flup .\\dj14\\Scripts\\pip install django-debug-toolbar .\\dj14\\Scripts\\pip install South Instalar la librería pil descargándola de: [https://www.pythonware.com/products/pil/](https://www.pythonware.com/products/pil/) Instalar la librería mysql-python de: [https://sourceforge.net/projects/mysql-python/files/latest/download](https://sourceforge.net/projects/mysql-python/files/latest/download) .\\dj14\\Scripts\\python manage.py syncdb .\\dj14\\Scripts\\python manage.py migrate

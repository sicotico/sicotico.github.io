---
layout: post
title: "Compilacion en QT4"
date: "2005-11-30"
categories: dev
---

Lo primero es una  introdución al trabajo con proyectos en qt4 , valido para qt3 .

Despeus de tener todo src la copilacion se hace con la herramienta qmake por lo general no se actualiza le enlace simbolico que apunta a qmake-qt3 y por tanto es aconsejable usar directamente qmake-qt4 "nombre del proyecto". Este problema tambien lo podemos tener con el compilador de objetos de QT , este se llama moc y pertence al paquete libqt4-dev . En este caso tenemso tambien un enlace simbolico en /usr/bin/moc que es el que usa por defecto qmake , por tanto aun que tnegamso qt4 instaldas no tiene porque usarlas para compilar . Asi que yo aconsejo aqui modificar el enlace simbolico  para que moc apunte a moc-qt4.

Para identificar el fallo ejecuta :

#qmake -v

Qmake version: 1.07a (Qt 3.3.4) Qmake is free software from Trolltech AS. #qmake-qt4 -v

QMake version: 2.00a Using Qt version 4.0.0 in /usr/lib

#moc -v

Qt Meta Object Compiler version 26 (Qt 3.3.4)

#moc-qt4

Qt Meta Object Compiler version 58 (Qt 4.0.0)

Con esta secuencia compruebas a donde apunta qmake y moc , y si tienes qmake-qt y moc-qt4

par acambiar  el enlace de moc seria

#ln -s /usr/bin/moc /usr/bin/moc-qt4

y para el de qmake

#ln -s /usr/bin/qmake /usr/bin/qmake4

\[  qmake-qt4 puedes no modifica su enlace pero el de moc es obligado ya que va a ser llamado desde qmake \] !!!! Recuerda que si kieres volver a compilar en qt3 debes modificar lso enlaces simbolicos otra vez ¡¡¡¡

Fallo encontrado enlas compilaciones de QT4 el fichero que genera como de proyecto se llama igual que la carpeta donde esta contenido, pero  con la extension "pro" , nosotros hemos de añadir la linea  {echo "QT += network" >> \*.pro} antes de ejecutar qmake-qt4 , un ejemplod efichero de compilacion seria

Ejemplo modificado del proyecto marabunta (https://apeiron.laotracara.com)

uic-qt4 marabunta\_gui.ui > marabunta\_gui.h qmake-qt4 -project

\# una linea necesaria que no es creada # por el comando anterior :S #es necesario que el fichero "pro" sobre el que #vamos a insertar la \* para k que no importe la carpeta donde este el prgrama

echo "QT += network" >> \*.pro qmake-qt4 make Todo esto ha sido hecho porque tuve este fallo mientras compilaba uan version de marabunta , espero que os sea de ayuda y si quereis pasar a ver el proyecto .

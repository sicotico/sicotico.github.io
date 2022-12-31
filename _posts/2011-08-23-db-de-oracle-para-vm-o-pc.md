---
layout: single
title: "DB de Oracle para VM o PC"
date: "2011-08-23"
categories: software
---

El titulo casi lo dice todo , normalmente tengo que instalar mucho software HP y claro la base de datos es Oracle. Si tienes un portátil aunque tenga 4 GB de RAM no deja de ser un equipo de potencia limitada , velocidad disco , etc ...

Un día sin querer , sin tomarlo ni beberlo me dice el DBA , oye quítale estas cosas que tu no las vas utilizar nunca y sino tienes un snapshot. Pues si básicamente es quitar esas opciones de recuperación flash , gestores de no se que y los datos de ehttps://luispuente.net/wp-admin/post.php?post=2223&action=edit&message=10jemplo o las plantillas. Iba a decir que la mitad de estas cosas no se lo que es pero en realidad es la mayoría.

Todo quedo registrado en un txt de eso que van de pc en pc y no te acuerda hasta que lo necesitas y te pasa horas buscando. Hoy toca publicarlo para que la búsqueda se reduzca a unos minutos.

Desde el menú de windows podemos acceder al "Asistente de configuración de Bases de Datos" , o utilizar el comando dbca

La acción que queremos realizar es crear un DB , así que estas son las opciones que debemos ir marcando

- Crear Base de Datos
- Uso General
- Nombre global , es el mismo que el SID
- Deshabilitamos el Enterprise Manager , es un gestor web para esta base de datos y consume muchos recursos.
- La contraseña pues esa típica que usa cada uno siempre.
- Marcamos la opción Sistema de Archivos. Porque son entorno Virtuales o de PCs personales.
- Seleccionamos la ruta de la DB

- lo normal es crearla dentro de la carpeta oracleoradata                                            Ej c:oracleproduct10.2.1db\_1 --> Motor de DB c:oracleoradata"nombre de DB" --> Mi DB
- La opción defecto es la que utilizo siempre para estos entornos.
- Desmarcar la opción "Especificar Área de Recuperación de Flash" , ocupa muchísimo y no lo se usar.
- Desmarcar la opción "Esquema de Ejemplo" , mi aplicación ya los creara o me dirá como , solo creamos la instancia en blanco.
- Nos informa de la memoria que queremos asignar , con la recomendación de hacerla lo mas pequeño posible para entorno de pruebas.
- El resto de pestañas viene por defecto y nos son validas .
- Revisamos varias paginar de resumen  .
- Marcamos la opción "Crear Base de Datos"
- Deshabilitamos las demás , no queremos scripts ni que sea plantilla

Gestión de DB Oracle

El Administrador de oracle es "Enterprise Manager Console" El administrador de oracle no registra las bases de datos y las tenemos que añadir a mano , la primera vez aparece un asistente.

Por si tenéis algún problema con los listener , os dejo otro post mas relacionado con el tema "[Oracle Listene](https://luispuente.net/2009/05/oracle-listener/ "Oracle Listener")r"

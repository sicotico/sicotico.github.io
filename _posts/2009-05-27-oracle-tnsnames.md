---
layout: single
title: "Oracle TNSnames"
date: "2009-05-27"
categories: software
---

En mi entorno de desarrolladores de oracle me pasaron el PL/SQL y el TOAD , si conocéis algún otro y que sea libre pos mejor ,dejad un comentario y listo.

Para que estos programan funciones , también el isqlplus , necesitas tener los tnsnames correctamente para que con un simple nombre sepa cual es el host y puerto a conectar.  Se configura mediante "Net Configuration Assistant"  y la opción "Configuración del Nombre del Servicio de Red Local".

Para verlo en modo "Hacker"  ( cosas de Saghul ) esta en el fichero

carpeta oracleproduct10.2.1cliente\_1ADMINNETWORKtnsnames.ora

Un fallo que me ha pasado es que no responde siempre si pones localhost  , asi que decidi pone rle nombre de maquina .

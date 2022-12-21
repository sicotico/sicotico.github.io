---
layout: post
title: "Time out en conexion por AJP"
date: "2010-01-26"
categories: dev
---

En este mundo tan complicado de las macro aplicaciones , resulta que tenemos que optimizar un enlace Apache + mod\_JK con un Tomcat mediante protocolo AJP.

En el fichero tomcat/conf/server.xml controlamos el time out de las sesiones , detalle importante ya que cada sesión puede generar conexiones a DB.

<!-- Define an AJP 1.3 Connector on port 8009 --> <Connector port="" enableLookups="false" redirectPort="" protocol="AJP/1.3" connectionTimeout="600000" />

`port` = Puerto donde se escucha `redirectPort` = Puerto donde reenviamos la petición

Fuente: [Tomcat Connector AJP](https://tomcat.apache.org/connectors-doc/ajp/ajpv13a.html)

---
layout: post
title: "Error en prolog de WDSL"
date: "2011-05-25"
categories: 
  - "sin-categoria"
---

Muchas veces los Web Service son la solución a la integración de herramientas , más bien la herramienta para que te fabriques tu propia integración. No es mi caso , pero no diré de este agua no beberé .  Teniendo dos herramientas que se comunican vía WDSL , la que recibe la conexión devuelve un error un poco criptico.

Cause by java.io.IOException: WSDLException: faultCode=PARSER\_ERROR: Problem parsing '<url>'.: Content is not allowed in prolog.

Resaltamos el erro ya que ha saltado una excepción pero no la han controlad:

**Content is not allowed in prolog.**

Pues con esta información he encontrado esta posible solución  , aunque el reinicio del Web Service soluciona este problema. Como trabajamos con cadenas y ficheros es normal que se generen caracteres extraños en el lado del servidor.

### [JAVA: Resolving org.xml.sax.SAXParseException: Content is not allowed in prolog](https://mark.koli.ch/2009/02/resolving-orgxmlsaxsaxparseexception-content-is-not-allowed-in-prolog.html)

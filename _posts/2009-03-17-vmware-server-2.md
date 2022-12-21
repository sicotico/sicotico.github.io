---
layout: post
title: "Vmware Server 2"
date: "2009-03-17"
categories: vmware
---

He migrado mis maquinas virtuales a la nueva versión y me he encontrado con muchisimos cambios.  Sobre todo en la usabilidad ,  los de marketing han realizado un modelo de negocio espectacular. Me explico , ahora la version server es gratis y tiene el mismo funcionamiento que Vmware Infraestructuras , con esto no me refiero a capacidades sino  al modelo de uso , yo puedo aprender con la  versión gratuita y luego manejar un entorno profesional.

El interface de manejo es web , y se le definen DataStores para imagenes ISO y porsupuesto par alas maquinas viertuales . Con esto lo que creamos son carpetas virtuales que se dirigen a partes del disco duro ,asi nosotros cuando creemos una maquina nueva con asignarla el Datastore ya sabe donde se situa. Vaya tonteria , pero si tenemos varios discos duros  independientes no tenemos porque crear capas a nivel de sistema operativo para crear volumenes logicos.

Se puede crear accesos directos a las maquinas virtuales tanto marcadores para el navegador como en el escritorio.

Un detalle muy empresarial es que segun se intala coge los credenciales de Admisnitrador de tu equipo , asi que si estas en dominio el admin de dominio puede controlar el VMWare Server 2.0 ,  vamos sino creas un perfil nuevo.

A parte se han cuidado de poder migrar las maquinas a Infraestrutura 3 sin problemas , bueno alguno saldra.

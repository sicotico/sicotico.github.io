---
layout: post
title: "VBS es una PUTA mierda"
date: "2008-11-11"
categories: dev
---

Despues de un mesecito haciendo scripts VBS , he tenido un remanso de paz para criticar este lenguaje fantástico para administradores de Windows. He hecho muchísimas pijadas y automatizado varios procesos y facilitado la ejecución de otros. Puedes instalar software modificar entradas del registro cambiar configuraciones del Windows en el entorno empresarial automatizar procesos nocturno es muy importante y bastante fácil de hacer. Ahora describamos algo importante , no hay documentación ordenada , se mezcla programación estructurada con orientación a objetos , básicamente es una aberración de métodos encapsulados en objetos que hay que instanciar primero y luego investigar si alguno de los métodos crea otro objeto para poder controlarlo . Mi ejemplo es el siguiente:

Para ejecutar programas externos utilizamos el objeto WScript.Shell , este proporciona el método Run y Exec .Pues bien la diferencia se marca en que Run lanza la ejecución controlada por un código , un integer y Exec devuelve un Objeto pero realiza el proceso a nivel de API , por lo que las configuraciones de sistema no le afectan , entre ellas la de seguridad .

Otro detalle es que a diferencia de un lenguaje como JAVA aquí no todos los objetos depende de WScript , sino que para acciones en sistema de ficheros instancias Scripting.FileSystemObject . Esto para mi es incomprensible.

Así hace las cosas Microsoft Visual Basic 6 era perfecto ya que generaba código con orientación a eventos y punto sin florituras , Visual Basic Script fue estructurado y muy bien ahora porque no terminan de migrar VBS a objetos que ya llevan más 2 añitos . Python se ha reescrito su API en 2 años

Pues yo en mi vida abandonaré el Shell script (Ksh , bahs ....) y menos una filosofía como la de Linux donde por lo menos se intentan hacer las cosas bien. Un detalle KSH pertenece a Unix System 5

---
layout: posts
title: "VBS ejecución desde en recursos compartidos"
date: "2008-11-11"
categories: dev
---

Estoy haciendo un script que des instale e instale software mediante capa WMI. Me he encontrado con el problema de las ejecuciones en red , Windows te pregunta si quieres ejecutarlo ya que esta en un localización no local . Yo quiero que sea autónomo resulta que hay dos métodos para realizar ejecuciones en VBS dependiendo de objetos o sin , claro esta no esta documentado porque es un lenguaje muy potente y maravilloso con el que puedes hacer casi de todo pero una "mierda de Microsoft" .

Si ejecutamos un setup.exe en remoto mediante Run este lo hará negociando con una Shell , pero simula una ejecución de doble clic con lo que aparece la ventanita de advertencia , pero si usamos Exec no falla , es porque Exec devuelve un objeto y Run un simple codigo , con el Exec deberemos de controlar la finalización de la ejecución con un bucle contra el atributo Status `Do While oExec.Status = 0 WScript.Sleep 100 Loop`

Fuentes:

[Exec Method](https://msdn.microsoft.com/en-us/library/ateytk4a(VS.85).aspx)

[Run Method](https://msdn.microsoft.com/en-us/library/d5fk67ky(VS.85).aspx)

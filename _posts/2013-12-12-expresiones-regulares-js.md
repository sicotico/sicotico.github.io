---
layout: post
title: "Expresiones regulares JS"
date: "2013-12-12"
categories: dev
---

## Pon expresiones regulares en tu vida

Tras unos días con Expresiones regulares terminas viendo patrones , si como si fuera matrix , pero en horizontal he resumido un detalle de código. Es un anota para la próxima vez que me vea con ello pueda saber un poco por donde empezar .

Lo primero es indicar la función principal , en este caso es la búsqueda y la sustitución de dicha búsqueda en todo el texto de entrada por un "Delimitador".

Lo segundo es traducir a lenguaje natural el "churro" de la expresión regular. Buscamos el patrón : ", Letras mayúscula y un igual"

Siguiendo con las partes he de indicar que en JS hay una función de remplazado , pero esta necesita retocar la expresión con los operadores de indica sustitución o sustitución global , como es este caso "/g"

`var separador = "|"; if(typeof(Delimitador) != "undefined"){ separador = Delimitador; }`

if (texto == "") { Response = "failure" } else { var expresion = /, (\[A-Za-z\]\*=)/g; var texto\_procesado = texto.replace(expresion,Delimitador + "$1"); Result = texto\_procesado; Response = "Success"; }

Después de revisar el código un par de veces desgranemos las Expresiones regulares usando esta como ejemplo. Es requisito tenerla encapsulada entre "/" , primordial , la "g" como dijimos antes es requisito de la función de remplazo . Ahora la explicación en pasos de dentro a fuera:

`[A-Za-z]*` Los corchetes define una palabra que posea mayúsculas y minúscula, numero indeterminado de letras en mayúsculas y/o minúsculas.

`([A-Za-z]*=)` Los paréntesis define la palabra anterior y que este seguida sin espacion de un signo de igual , "="

`, ([A-Za-z]*=)`

Si hay un espacio en blanco porque yo buscaba dicho espacio al inicio , así que forma parte del patrón.

Con esto y un bizcocho tenemos un ejemplo para entender un poco las expresiones regulares y sobre todo para utilizarlas en JS

Fuentes:

[Regular Expression (Objeto de JavaScript)](https://msdn.microsoft.com/es-es/library/ie/h6e2eb7w%28v=vs.94%29.aspx "Regular Expression (Objeto de JavaScript)")

[RegExp (Objeto de JavaScript)](https://msdn.microsoft.com/es-es/library/ie/9dthzd08%28v=vs.94%29.aspx "RegExp (Objeto de JavaScript)")

[Replace (Objeto String)](https://msdn.microsoft.com/es-es/library/ie/t0kbytzc%28v=vs.94%29.aspx "replace (Método, String de JavaScript)")

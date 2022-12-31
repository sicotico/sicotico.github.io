---
layout: single
title: "Temas hijo en WP"
date: "2011-12-11"
categories: dev
---

Siendo un poco tarde  , estoy revisando como se crean los temas hijo , la forma correcta de desarrollar en Wordpress.

Las reglas básicas de los temas hijo de WordPress son las siguientes:

El archivo hijo style.css no llama al archivo style.css padre así que debemos importarlo como se indica arriba. Cada archivo php del tema hijo sustituye al mismo archivo php del tema padre. El archivo functions.php es un caso especial. Primero se llama al del hijo luego al del padre. Esta premisa mantiene el fichero de funciones intacto en las actualizaciones del theme padre. Ademas nos obliga a que no exista nombres de funciones iguales entre los themes.

Para empezar deberemos de montar esta estructura de carpetas

**theme\_hijo** (carpeta)

- _style.css_ (obligatorio)
- _functions.php_ (opcional
- _screenshot.png_ (opcional)

Esto creo que es muy poco explicito , así que he traducido la pagina de la documentación oficial.

_**Traducción , "propia" , de la pagina oficial**_

# Temas hijo

Idiomas: Inglés • 日本语 • Français • Português do Brasil • Русский • Slovenčina • ไทย • 中文 (简体) • (tu idioma)

## Contenido

1. Estructura de directorios
2. El archivo _style.css_ necesario
3. Ejemplo de un tema básico para niños

1. Nota sobre la regla @ import
2. Nota sobre el apoyo RTL
3. Nota sobre _Twenty Eleven_ y con el Dark Theme o la opción Link Color

> - _functions.php_ uso

1. Referencias / Incluye los archivos en su tema infantil
2. Uso de formatos de mensaje

> - Los archivos de plantilla
> - Otros archivos
> - Recursos

 

 

Un tema hijo de WordPress es un tema que hereda la funcionalidad de otro tema, llamado el tema principal, y le permite modificar o añadir,  funcionalidades al tema padres. En este artículo se muestra cómo crear un tema hijo básico  y explica lo que puedes hacer con él. Como tema principal ejemplo que utiliza es _Twenty Ten_, el nuevo tema por defecto de WordPress 3.0.

Hacer un tema hijo es muy simple. Cree un directorio, coloque un archivo style.css el formato correcto y usted tiene un tema hijo! Con un poco de comprensión de HTML y CSS, puede hacer que el tema hijo básico modifique el estilo y el diseño dl tema principal en la medida necesaria , evitando editar los archivos del tema de los padres en sí. De esta manera, cuando el tema principal se actualiza, las modificaciones se conservan.

**Por esta razón, los temas hijo son la forma recomendada de hacer modificaciones a un tema.**

Con un conocimiento básico de PHP, plantillas de WordPress, y el API Plugin de WordPress, puede hacer que el tema hijo se extienden prácticamente todos los aspectos de un tema principal, y otra vez, sin modificar los archivos del tema principal.

 

# Estructura de directorios

Un tema hijo reside en su propio directorio en wp-content/themes. El siguiente esquema muestra la ubicación de un tema hijo, junto con su tema principal (Twenty Ten) en una estructura de directorios típico de WordPress:

- public\_html

- wp-content

- themes (directorio donde están todos los temas)

- TwentyTen (directorio de nuestro tema principal ejemplo, Twenty Ten)

- TwentyTen hijo (directorio de nuestro tema de niños, se puede llamar de cualquier manera)

- style.css (archivo requerido en un tema menor, debe ser llamado style.css)

Este directorio puede contener tan sólo un archivo style.css, y tanto como cualquier otro tema de WordPress :

1. style.css (requerido)
2. functions.php (opcional)
3. Los archivos de plantilla (opcional)
4. Otros archivos (opcional)

Vamos a ver cómo es cada una de estos ficheros.

## El archivo style.css (necesario)

style.css es el único que se requiere en un tema hijo. Se ofrece la información del encabezado por el cual reconoce el tema de WordPress  y que sustituye el style.css de los padres.

Como con cualquier tema de WordPress, la cabecera de la información debe estar en la parte superior del archivo, la única diferencia es que en un tema menor la plantilla: la línea es necesaria, por lo que WordPress sabe que tema es el padre de la temática infantil.

He aquí un ejemplo de información de cabecera style.css un tema menor:

/ \*
Nombre del tema: Veinte Once Niños
URI tema: https://example.com/
Descripción: tema infantil para el siglo XXI Once tema
Autor: Su nombre aquí
URI Autor: https://example.com/about/
Plantilla: twentyeleven
Versión: 0.1.0
\* /

Una breve explicación de cada línea:

- Nombre de tema. (Se requiere) Niño nombre del tema.
- Tema URI. (Opcional) Niño página web el tema.
- Descripción. (Opcional) ¿Qué es este tema. Por ejemplo: Mi tema de su primer hijo. ¡Hurra!
- Autor URI. (Opcional) Autor página web.
- Autor. (Opcional) Nombre del autor.
- Plantilla. (Se requiere) nombre del directorio del tema de los padres, mayúsculas y minúsculas.

- NOTA. Usted tiene que cambiar a un tema diferente y de nuevo al tema hijo cuando se modifica esta línea.
- Versión. (Opcional)  Versión del tema hijo . Por ejemplo: 0.1, 1.0, etc

La parte posterior al cierre \* / de la cabecera funciona como un archivo de hoja de estilo . Es donde se situan las reglas de estilo que desee aplicar a WordPress.

Tenga en cuenta que un tema de estilos hijo reemplaza la hoja de estilos de los padres por completo. (Hoja de estilo de los padres no se carga en absoluto por WordPress.) Por lo tanto, si simplemente desea modificar algunas pequeñas cosas en el estilo y el diseño de la cosa de padres en lugar de hacer desde cero, tiene que importar de forma explícita la hoja de estilos de el padre, y luego añadir las modificaciones. El siguiente ejemplo muestra cómo utilizar la regla @ import para hacer eso.

### Ejemplo de un tema hijo básico

Nuestro tema principal para este ejemplo es Veinte Once. Que más nos gusta todo lo relacionado con ella, excepto el color del título del sitio, que queremos cambiar de negro a verde. El uso de un tema menor, todo lo que necesita es de tres sencillos pasos:

1. Crea un nuevo directorio en wp-content/themes, y el nombre de twentyeleven-hijo (o lo que quieras).
2. Guardar el código de abajo en un archivo llamado style.css, y situarlo  en el nuevo directorio.
3. Ir al panel> Temas y activar su nuevo tema, el Twenty Ten Niño.

/ \*
Nombre del tema: Twentyeleven Niño
Descripción: Niño tema para el tema twentyeleven
Autor: Su nombre aquí
Plantilla: twentyeleven
\*

@ Import url ("../ twentyeleven / style.css ");

# Site-un título {
color: # 009900;
}

Esto es lo que el código anterior es así, paso a paso:

1. / \* Abre el tema de cabecera del niño de la información.
2. `Theme Name`: declara el nombre del tema del niño.
3. `Description:`describe cuál es el tema. (Opcional, se puede omitir).
4. `Author:`declara el nombre del autor. (Opcional, se puede omitir).
5. `Template:`declara el padre del tema del niño, es decir, el directorio del tema que el niño utiliza las plantillas.
6. `*/` Cierra la cabecera del hijo de la información.
7. The `@import`@ rule trae estilos de los padres.
8. The `#site-title a` rule define un color (verde) para el nombre del sitio, haciendo caso omiso de la regla correspondiente de los padres.

### Nota sobre la regla @ import

### No debe haber otras reglas CSS por encima de la regla @ import. Si poner otras reglas por encima de ella, será invalidada y la hoja de estilos de los padres no se importará.

### Nota sobre el apoyo RTL

Para apoyar a las lenguas RTL, añadir archivos rtl.css a su tema infantil, que contiene:

/ \*
Nombre del tema: Twenty Ten Niño
Plantilla: twentyeleven
\* /

@ Import url ("../ twentyeleven / rtl.css ");

WordPress carga automática de archivos rtl.css sólo si is\_rtl (). Incluso si el tema de los padres no tiene ningún archivo rtl.css, se recomienda agregar el archivo a su tema.

### Nota sobre Veinte Once y usando el tema Dark o la opción Color de Enlace

La hoja de estilos twenty eleven dark y la link color option se cargan después de  tema hijo, por lo tanto, algunos cambios de color no puede mostrar como se cargan antes.

No hay necesidad de cambiar la hoja de estilo oscuro o código en el directorio padre veinte once, como se puede corregir esta dando la prioridad al cambio de color, lo hacemos mediante la adición de !important en el estilo.

Aquí vamos a cambiar el color del título del sitio, y el negar el título del sitio hover color, si no nos gusta el color o el título que se muestra como un enlace.

/ \*
Nombre del tema: Veinte Once Niños
Descripción: tema infantil para el siglo XXI Once tema
Autor: Su nombre aquí
Plantilla: twentyeleven
\* /

@ Import url ("../ twentyeleven / style.css ");

/ \* Esto anulará el color del título del sitio, incluso en el tema oscuro \* /
# Site-un título {
color: # 009900 importante;!
}

/ \* Esto anulará el color de los enlaces cambiado \* /
# Site-un título: el foco,
# Site-título a: hover,
# Site-título a: active {
color: # 009900 importante;!
}

Los colores de estilo seleccionado con _!important_ no serán cambiado por el theme Utilizando _functions.php_

A diferencia de _style.css_, el _functions.php_ del tema del niño no anula su contraparte de los padres. En su lugar, se carga, además de functions.php los padres. (En concreto, se carga justo antes de que el archivo de los padres.)

De esta manera, el functions.php del tema hijo ofrece un inteligente y sin problemas método para modificar la funcionalidad de un tema de los padres. Digamos que usted desea agregar una función de PHP a su tema. La forma más rápida sería la de abrir su archivo functions.php y poner la función allí. Pero eso no es inteligente: La próxima vez que se actualiza el tema, su función va a desaparecer. Pero hay una alternativa que es la manera más inteligente: se puede crear un tema menor, agregar un archivo functions.php en él, y añadir la función de ese archivo. La función va a hacer exactamente el mismo trabajo a partir de ahí también, con la ventaja de que no se verán afectados por las futuras actualizaciones del tema de los padres.

La estructura de functions.php es simple: Una etiqueta de apertura de PHP en la parte superior, una etiqueta PHP cierre en la parte inferior, y, entre ellos, sus pedacitos de PHP. En ella se puede poner funciones como tantos o tan pocos como desee. El siguiente ejemplo muestra un archivo functions.php elemental que hace una cosa simple: Agrega un enlace favicon para el elemento de encabezado de las páginas HTML.

favicon\_link función () {
"rel="shortcut <link icon" type="image/x-icon" href="/favicon.ico" /> eco. " N";
}
add\_action ('wp\_head', 'favicon\_link');

CONSEJO PARA DESARROLLADORES DE TEMAS. El hecho de que en un tema hijo se carga primero functions.php significa que usted puede hacer las funciones de usuario de su tema , es decir, sustituible por un tema-por el hijo declarando que de forma condicional. Por ejemplo:

if (! function\_exists ('theme\_special\_nav')) {
theme\_special\_nav función () {
/ / Hacer algo.
}
}

De esta manera, un tema menor puede sustituir una función PHP de los padres con sólo declarar de nuevo.

### Referencia a / Incluye los archivos en su tema infantil

Cuando es necesario incluir los archivos que residen dentro de la estructura de directorio de su tema hijo, va a utilizar get\_stylesheet\_directory (). Debido a style.css de la plantilla de los padres se sustituye por style.css el tema del niño, y su style.css reside en la raíz de los puntos de subdirectorio, get\_stylesheet\_directory () el tema del niño en el directorio de su tema del niño (no el directorio el tema de los padres).

He aquí un ejemplo, usando require\_once, que muestra cómo se puede utilizar get\_stylesheet\_directory al hacer referencia a un archivo almacenado en la estructura de directorio de su tema de los niños.

require\_once (get\_stylesheet\_directory () '/ my\_included\_file.php.);

#### Utilizando post con formato

Un tema secundario hereda los formatos de mensaje definidos por el tema de los padres. Pero, al crear temas niño, tenga en cuenta que el uso de add\_theme\_support ('post-formatos') se anulará el formato definido por el tema de los padres, para no agregar a ella.

### Los archivos de plantilla

Plantillas en un tema hijo se comporte como style.css, en que caso omiso de sus homónimos de los padres. Un tema hijo puede anular cualquier plantilla de los padres por el simple uso de un archivo con el mismo nombre. (NOTA. index.php puede ser evitado sólo en WordPress 3.0 y posteriores.)

Una vez más, esta característica WordPress te permite modificar las plantillas de un tema de los padres sin llegar a la edición, por lo que sus modificaciones se conservan cuando el tema principal se actualiza.

Aquí están algunos ejemplos de casos para el uso de archivos de plantilla en un tema menor:

- Para añadir una plantilla que no es ofrecido por el tema de los padres (por ejemplo, una plantilla para una página de mapa, o para una sola columna páginas, que estarán disponibles para seleccionar en la pantalla de Editar).
- Para añadir una plantilla de más específicos (ver Jerarquía de plantilla) de lo que los padres usan (por ejemplo, una plantilla de tag.php a utilizar para los archivos en lugar de la etiqueta archive.php genérico de la matriz).
- Para reemplazar una plantilla de la matriz (por ejemplo, hacer su propia home.php para anular home.php de los padres).

### Otros archivos

Además de style.css, functions.php, y los archivos de plantilla como index.php, y home.php, un tema niño puede usar cualquier tipo de archivo uso de pleno derecho los temas, siempre y cuando el archivo esté bien ligado. Por ejemplo, un tema niño puede usar los iconos y las imágenes que están vinculadas a su hoja de estilo, archivos JavaScript enlazadas desde la parte superior o inferior de las páginas, o extra archivos PHP llamado desde sus plantillas o de su archivo functions.php.

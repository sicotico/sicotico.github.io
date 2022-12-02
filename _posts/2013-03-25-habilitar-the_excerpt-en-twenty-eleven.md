---

title: "Habilitar the_excerpt() en Twenty Eleven"
date: "2013-03-25"
categories: 
  - "sin-categoria"
---

Estoy investigado el tema **Twenty Eleven** y me he dado cuenta de lo amplio que es. Llevo un par de mejoras y esta ultima me ha costado un poco  , no he hecho caso a Feliz Zapata y no tengo la jerarquía de páginas de wordpress a mano.

Mi intención es habilita en el home del tema el modo resumen para las entradas. Eso de poner la etiquete  a mano cuando editas un post es trabajo que se puede automatizar. La idea es sencilla , cambia la funcion **_the\_content()_** por **_the\_excerpt()_**. Y el problema me llegó al abrir el **_loop_** principal de index.php , no se parece en nada a los que había visto.

 

El original:

 

En este caso tenemos el _get\_template\_part_ que no dirige al fichero **_content.php._** En este fichero buscamos la sección

//.....

Ahora comentamos la función

Y generamos otra linea sustituyendo simplemente the\_content por the\_excerpt

Para ajustar la cantidad de texto a mostrar con nuestro diseño podemos limitar el numero de palabras a mostrar. Para ello nos valemos de un filtro en _**functions.php**_

function custom\_excerpt\_length( $length ) {
	return 20;
}
add\_filter( 'excerpt\_length', 'custom\_excerpt\_length', 999 );

Utilizamos el filtro **'excerpt\_length'**

**Nota:** _Para cambiar el mensaje de "Continue reading" debemos hacerlo en los ficheros de traducción a código a FUEGO , por eso de tener algo de estilo y no chapucear el código_

 

**Fuentes:**

Propia experiencia

[Function Reference/the excerpt](https://codex.wordpress.org/Function_Reference/the_excerpt "the_excerpt")

[Linkdin Wordpress en español](https://www.linkedin.com/groups/theexcerpt-Dudas-1242577.S.217068434?qid=9cdce20a-7350-49ca-aee4-87146497b034&trk=group_most_popular-0-b-ttl&goback=.gmp_1242577 "[the_excerpt()] Dudas ")

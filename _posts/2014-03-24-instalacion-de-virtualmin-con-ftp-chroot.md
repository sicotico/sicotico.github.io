---

title: "Instalación de Virtualmin con FTP chroot"
date: "2014-03-24"
categories: 
  - "sin-categoria"
---

Estos días he estado preparando un servidor con Virtualmin. Va a ser mi laboratorio de pruebas , webmin y yo somos amigos desde hace muchos años y esta evolución me ha empezado ser interesante. Me estoy haciendo profesional y muchas tareas las puedes hacer a mano o con interfaz web así que  en vez de picar scripts  estoy aprendiendo a usar esta interfaz sobre una Ubuntu 12.04.2 LTS.

La Instalación de Virtualmin con FTP chroot es sencilla siempre que cumplas con la lista de SO compatibles , cosa que no hice en primera instancia  y toco formatear todo y volver a empezar.

[Manual de referencia para la instalación fácil , con script.](https://www.virtualmin.com/documentation/installation/automated "Automated Virtualmin Installation")

Tras el típico siguiente siguiente que deberíamos de leer , viene la parte de como quieres que este configurado tu virtualmin A base de preguntas sobre módulos adicionales los habilitas y estableces como deben de comportarse:

- mail
- antivirus
- DNS

Principalmente  la opción más importante  es subirlos memoria ram para que vayan más rápido , si tienes ram de sobra lo podrás hacer sino  ajo y agua. Yo trabajo sobre 2 GB de RAM y lo he subido todo a memoria.

Ahora con la instalación de Virtualmin con FTP chroot debemos configurar lo. Desde el modo sencillo , busquemos las opciones en la interfaz que nos permitan dar seguridad a nuestros usuarios.

No es de recibo que un usuario con ftp pueda ver todas las cuentas registradas en el servidor , hay que "enjaularlo" , es un proceso muy sencillo y nativo en sistemas NIX\* . Se llama "chroot" , cambio de raiz ,  ahora necesitamos que los usuario tengan como raiz su directorio home. De esta forma no podrán desplazarse un nivel inferior y ver las cuentas del servidor.

Esto que parece algo importante y que siempre debemos de hacer resulta extremadamente sencillo , Virtualmin lo tiene implementado de forma gráfica y con apenas un par de click , así que  no tienes sentido no hacerlo.

Instrucciones:

En nuestro panel de administración de Virtualmin desplegamos el menú "Limits and Validation" , en la ultima opción "$chroot\_title" marcamos la opción que deseemos para los servidores que queramos y listo.

### Fuentes:

[Documentación oficial ProFTPd](https://www.proftpd.org/docs/howto/Chroot.html "Documentación oficial ProFTPd")

[Restringir acceso FTP en Virtualmin](https://fruteroloco.es/content/restringir-acceso-ftp-en-virtualmin "restringir-acceso-ftp-en-virtualmin")

---
layout: post
title: "VSFTPD Very Secure FTP"
date: "2006-11-27"
categories: 
  - "sin-categoria"
---

## "Obra adaptada a Ubuntu/Debian"

**Introducción.**

FTP (**F**ile **T**ransfer **P**rotocol) o Protocolo de Transferencia de Archivos (o ficheros informáticos) es uno de los protocolos estándar más utilizados en Internet siendo el más idóneo para la transferencia de grandes bloques de datos a través de redes que soporten TCP/IP. El servicio utiliza los puertos 20 y 21, exclusivamente sobre TCP. El puerto 20 es utilizado para el flujo de datos entre cliente y servidor. El puerto 21 es utilizando para el envío de órdenes del cliente hacia el servidor. Prácticamente todos los sistemas operativos y plataformas incluyen soporte para FTP, lo que permite que cualquier computadora conectada a una red basada sobre TCP/IP pueda hacer uso de este servicio a través de un cliente FTP.

VSFTPD (**V**ery **S**ecure **FTP** **D**aemon) es un sustento lógico utilizado para implementar servidores de archivos a través del protocolo FTP. Se distingue principalmente porque sus valores por defecto son muy seguros y por su sencillez en la configuración, comparado con otras alternativas como Wu-ftpd. Actualmente se presume que VSFTPD es quizá el servidor FTP más seguro del mundo.

## Sustento lógico necesario.

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>sudo aptitude install vsftpd</pre></td></tr></tbody></table>

## Ficheros de configuración.

<table border="0" cellpadding="4" cellspacing="4" width="100%"><tbody><tr><td bgcolor="#efefef" valign="top" width="26%"><pre>/etc/vsftpd.user_list</pre></td><td bgcolor="#efefef" valign="top" width="74%">Lista que definirá usuarios a enjaular o no a enjaular, dependiendo de la configuración.</td></tr><tr><td bgcolor="#efefef" valign="top" width="26%"><pre>/etc/vsftpd.conf</pre></td><td bgcolor="#efefef" valign="top" width="74%">Fichero de configuración.</td></tr></tbody></table>

## Procedimientos.

Utilice un editor de texto y modifique el fichero **/etc/vsftpd/vsftpd.conf**. A continuación analizaremos los parámetros a modificar o añadir, según serequiera para necesidades particulares.

### Parámetro anonymous\_enable.

Se utiliza para definir si se permitirán los accesos anónimos al servidor. Establezca como valor **YES** o **NO** de acuerdo a lo que se requiera.

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>anonymous_enable=YES</pre></td></tr></tbody></table>

### Parámetro local\_enable.

Es particularmente interesante si se combina con la función de jaula (**chroot**). Establece si se van a permitir los accesos autenticados de los usuarios locales del sistema. Establezca como valor **YES** o **NO** de acuerdo a lo que se requiera.

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>local_enable=YES</pre></td></tr></tbody></table>

### Parámetro write\_enable.

Establece si se permite el mandato **write** (escritura) en el servidor. Establezca como valor **YES** o **NO** de acuerdo a lo que se requiera.

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>write_enable=YES</pre></td></tr></tbody></table>

### Parámetro ftpd\_banner.

Este parámetro sirve para establecer el banderín de bienvenida que será mostrado cada vez que un usuario acceda al servidor. Puede establecerse cualquier frase breve que considere conveniente.

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>ftpd_banner=Bienvenido al servidor FTP de nuestra empresa.</pre></td></tr></tbody></table>

### Estableciendo jaulas para los usuarios: parámetros chroot\_local\_user y chroot\_list\_file.

De modo predeterminado los usuarios del sistema que se autentiquen tendrán acceso a otros directorios del sistema fuera de su directorio personal. Si se desea recluir a los usuarios a solo poder utilizar su propio directorio personal, puede hacerse fácilmente con el parámetro **chroot\_local\_user** que habilitará la función de **chroot()** y los parámetros chroot\_list\_enable y chroot\_list\_file para establecer el fichero con la lista de usuarios que quedarán excluidos de la función **chroot()**.

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd/vsftpd.chroot_list</pre></td></tr></tbody></table>

Con lo anterior, cada vez que un usuario local se autentique en el servidor FTP, solo tendrá acceso a su propio directorio personal y lo que este contenga. **No olvide crear el fichero** **/etc/vsftpd/vsftpd.chroot\_list**, ya que de otro modo no arrancará el servicio vsftpd.

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>touch /etc/vsftpd/vsftpd.chroot_list</pre></td></tr></tbody></table>

### Control del ancho de banda.

#### Parámetro anon\_max\_rate.

Se utiliza para limitar la tasa de transferencia en bytes por segundo para los usuarios anónimos, algo sumamente útil en servidores FTP de acceso público. En el siguiente ejemplo se limita la tasa de transferencia a 5 Kb por segundo para los usuarios anónimos:

| anon\_max\_rate=5120 |
| --- |

#### Parámetro local\_max\_rate.

Hace lo mismo que anon\_max\_rate, pero aplica para usuarios locales del servidor. En el siguiente ejemplo se limita la tasa de transferencia a 5 Kb por segundo para los usuarios locales:

| local\_max\_rate=5120 |
| --- |

#### Parámetro max\_clients.

Establece el número máximo de clientes que podrán acceder simultáneamente hacia el servidor FTP. En el siguiente ejemplo se limitará el acceso a 5 clientes simultáneos.

| max\_clients=5 |
| --- |

#### Parámetro max\_per\_ip.

Establece el número máximo de conexiones que se pueden realizar desde una misma dirección IP. Tome en cuenta que algunas redes acceden a través de un servidor proxy o puerta de enlace y debido a esto podrían quedar bloqueados innecesariamente algunos accesos. en el siguiente ejemplo se limita el número de conexiones por IP simultáneas a 5.

| max\_per\_ip=5 |
| --- |

## Aplicando los cambios.

A diferencia de otros servicios FTP, VSFTPD no requiere configurarse como servicio sobre demanda. Por lo tanto no depende de servicio **xinetd**. La versión incluida en distribuciones como Red Hat™ Enterprise Linux 3.0 y White Box Enterprise Linux 3.0 puede inicializarse, detenerse o reinicializarse a través de un guión similar a los del resto del sistema. De modo tal, podrá inicializarse, detenerse o reinicializarse a través del mandato **service** y añadirse al arranque del sistema en un nivel o niveles de corrida en particular con el mandato **chkconfig**.

Para ejecutar por primera vez el servicio, utilice:

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>sudo /etc/init.d/vsftpd start</pre></td></tr></tbody></table>

Para hacer que los cambios hechos a la configuración surtan efecto, utilice:

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>sudo /etc/init.d/vsftpd restart</pre></td></tr></tbody></table>

Para detener el servicio, utilice:

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>sudo /etc/init.d/vsftpd stop</pre></td></tr></tbody></table>

Para añadir VSFTPD al arranque del sistema en todos los niveles de corrida, utilice:

<table bgcolor="#efefef" border="0" cellpadding="4" cellspacing="0" width="85%"><tbody><tr><td valign="top" width="100%"><pre>aptitude realiza esta accion automaticamente , sino ejecute esta orden :</pre><pre>sudo update-rc.d vsftpd defaults</pre></td></tr></tbody></table>

## _\*Respecto el manejo de servicios recomiendo leer_

## _[Servicos Ubuntu](https://sicotico.wordpress.com/2005/07/21/servico-ubuntu/ "Enlace Permanente a Servicos Ubuntu")_

**Modificaciones necesarias en el muro cortafuegos.**

Si se utiliza un cortafuegos con políticas estrictas, como por ejemplo **Shorewall**, es necesario abrir los puerto 20 y 21 por TCP (**FTP-DATA** y **FTP**, respectivamente).

Las reglas para el fichero **/etc/shorewall/rules** de **Shorewall** correspondería a algo similar a lo siguiente:

<table bgcolor="#e6e6e6" border="0" cellpadding="3" cellspacing="0" width="85%"><tbody><tr><td valign="top"><pre>#ACTION	SOURCE	DEST	PROTO 	DEST		SOURCE
#				PORT		PORT(S)1
ACCEPT	net	fw	tcp	20,21
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE</pre></td></tr></tbody></table>

Fuente Original:

**Autor:** Joel Barrios Dueñas **Correo electrónico:** [joelbarrios arroba linuxparatodos punto net](https://www.linuxparatodos.net/geeklog/forum/)

**Sitio de Red:** [https://www.linuxparatodos.net/](https://www.linuxparatodos.net/) **Jabber ID:** darkshram@jabber.org

**Creative Commons [Reconocimiento-NoComercial-CompartirIgual 2.1](https://creativecommons.org/licenses/by-nc-sa/2.1/es/)**

> © 1999-2005 Linux Para Todos. Usted es libre de copiar, distribuir y comunicar públicamente la obra y hacer obras derivadas bajo las condiciones siguientes: a) Debe reconocer y citar al autor original. b) No puede utilizar esta obra para fines comerciales. c) Si altera o transforma esta obra, o genera una obra derivada, sólo puede distribuir la obra generada bajo una licencia idéntica a ésta. Al reutilizar o distribuir la obra, tiene que dejar bien claro los términos de la licencia de esta obra. Alguna de estas condiciones puede no aplicarse si se obtiene el permiso del titular de los derechos de autor. Los derechos derivados de usos legítimos u otras limitaciones no se ven afectados por lo anterior. Licencia completa en [castellano](https://creativecommons.org/licenses/by-nc-sa/2.1/es/legalcode.es). La información contenida en este documento y los derivados de éste se proporcionan tal cual son y los autores no asumirán responsabilidad alguna si el usuario o lector hace mal uso de éstos.

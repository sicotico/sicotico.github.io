---

title: "Administración Remota"
date: "2007-04-02"
categories: 
  - "sin-categoria"
---

Hoy ha tocado añadir nuevos contenidos , así que he unificado todo lo que he hecho yo para manejar mi server de forma remota. Hay que tener en cuenta los estudios y no perder tiempo en nimiedades.

1 Experiencias en servicio DDNS

1.1 Cliente software

Bajo esa premisa intenta hacer mi ip dinámica de ono en estática , mediante servicio DDNS , los servicio que probé son:

DSLAND.org y el mítico DYNDNS.org , estando dentro de una NAT el cliente de actualización (ddclient , en repositorios) hay que modificarlo parra que obtenga la ip publica ya que por defecto se la solicita la interface de red , en el caso de DSLAND son mas rustico , te explican que linea tienes que añadir al crontab , vamos automatizan una consulta con parámetros a su web (links) para actualizar tu ip.

Personalmete es mas simple DSLAND pero me falló mucho.

1.2 Uso del router como cliente

Mi instalación es la siguiente:

Mi router de conceptronic enganchado al cable-modem de ono mediante clavija de amplicación normalmente la clavija 1 sino viene con el nombre de "uplink" .

Este router esta configurado con DHCP contra el cable módem así que posee la ip externa.

Dentro de las mil opciones que no sabemos usar y una de ellas es que el actualice la ip contra un servicio DDNS , por consiguiente yo encontré la opción mirando en los nombres donde apareciera la subcadena "dns" ignorando mayúsculas , magia con estar registrando en algún servicio soportado por tu router y dando los datos de dominio , user y pass de tu dominio el router te hará estática tu ip.

2 Herramientas básicas de control

VNC y SSH son sagradas en esta actividad.

VNC se divide en dos aplicaciones servidor y una cliente , el servidor es el ordenador al que vas a acceder y el cliente es cualquier que posea un software para este protocolo. Con esto solo hace falta configurar el servidor.

Si eres usuario novel Ubuntu trae preinstalado un xvncserver , para activarlo :

Sistema --> Preferencias --> Escritorio Remoto

Ahora solo permite que compartir tu escritorio , por ahora solo lo podrán ver ,¡¡¡ Cuidado hay que activar las opciones de seguridad !!!!! , la clave es primordial si lo vas a usar a través de internet.

Para este protocolo hay que abrir el puerto 5900 en el router , a ser posible con protocolos TCP y UDP

SSH (Secure SHELL) es mas profesional , ya que se maneja en cosola aumentado la rapidez y la complejidad para acciones comunes con el ratón , es todo menos atractivo para el usuario.

lo basico es intlarselo , existente en paquetes binarios para todas las distribuciones del mundo mundial , lo basico es comprender que vas a usar la consola del otro ordenador y va ser enviado todo bajo cifrado , importante entender que tu no envias una orden sino que escribes la orden directamente allí. El nombre de usuario no lo solicita por defecta ya que toma el usuaario de tu maquina local , si no existe el usuario local en el servidor nunc apodras acceder , asi que existe el parametro -l "nombre de usuario" para indicar que cuenta del servidor quieres usar. Esta herramienta parece algo simpre envio de texto cibfrado que se ejecuta en el remoto , pero es más aun. Puedes exportar ventanas X redirigiendo hacia tu equipo local , el ejemplo es sencillo :

Te conectas por ssh a tu maquina remota , ejecutas un firefox desde consola y se te abria en local usando los los binarios del servido , basicamente solo ves las ventanas , todos los evento generados por dicha aplicacion sera controlados por la maquina remota.

Todavía queda por decir la mayor maravilla de esta herramienta , Tunel SSH , da soporte cifrado de acceso a aplicaciones

[![ssh02.jpg](images/ssh02.thumbnail.jpg)](https://sicotico.files.wordpress.com/2007/03/ssh02.jpg "Enlace directo a archivo")

Ejemplos de syntaxis:

ssh -l "nombre de usuario" "ip del servidor"

ssh -l "nombre de usuario" -X "ip del servidor" (atentos que la "X" es mayúscual)

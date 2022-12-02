---

title: "Instalación y Configuración de FreeNX en Ubuntu"
date: "2007-12-06"
categories: 
  - "sin-categoria"
---

Para todos aquellos que pasan por aquí y usan Linux les brindo un mino HowTo para el control remoto de sus maquinas Linux.

Este software como hemos avanzado realiza control remoto de maquinas mediante el acceso a escritorio remoto . Especificamos que FreeNX no utiliza un protocolo como VNC o escritorio remoto de Windows todos ellos basado RBD (Remote Frame Buffer).La empresa NoMachine diseño un protocolo basado a nivel de red en SSH y a nivel de datos en X-Windows. Esto quiere decir que las transmisiones se relizan bajo SSH , utiliza las cuentas de usuario , la encriptación y las herramientas de seguridad que nos brinda esta maravillosa herramienta.El nivel de datos es que la informacián que se transmite no son imágenes sino meta-datos de X-Windows reduciendo así la cantidad de datos a enviar , esto es lo bueno de X-Windows con conexiones de 56K se pueden controlar sesiones remotas por tanto solo es valido para maquinas servidoras con sistemas X-Windows.

**_Guia de instalación:_**

**_1 - Preparación_**

_**1.1 Activar Repositorios**_

_"Seveas" :_

_echo "deb https://mirror.ubuntulinux.nl dapper-seveas all" > /etc/apt/sources.list_

_echo "src-deb https://mirror.ubuntulinux.nl dapper-seveas all" > /etc/apt/sources.list_

_sudo gpg --keyserver subkeys.pgp.net --recv-keys 1135D466_

_sudo gpg --export --armor 1135D466 | sudo apt-key add -_

_sudo aptitude update_

**_1.2 Descarga manual de paquetes_**

Utilizando un navegar podemos obtener los paquetes desde esta URL:

https://mirror.ubuntulinux.nl/dists/feisty-seveas/freenx/

https://mirror.ubuntulinux.nl/dists/dapper-seveas/

https://mirror.ubuntulinux.nl/dists/gutsy-seveas/

**_2 - Requisitos de nuestro servidor SSH_**

**_2.1 - Puerto de nuestro servidor_**

Ahora verifiquemos que SSH esta en el puerto 22 , tened en cuenta que FreeNx necesita saber necesariamente donde esta escuchando SSH , FreeNX cree que el ssh esta en ese puerto por defecto.

_#grep -i port /etc/ssh/sshd\_config_

La salida correcta es esta:

_\# What ports, IPs and protocols we listen for_

_#Port 22_

En caso contrario modificar la linea:

_\# SSHD\_PORT=22 , quitando el comentario y cambiamos 22 por el puerto que tengamos nuestro ssh , al final ha de quedar_

SSHD\_PORT =

**_2.2 - Claves Públicas de nuestro servidor_**

También hemos de comprobar que ssh tenga activadas las claves públicas

_#grep -i PubkeyAuthentication /etc/ssh/sshd\_config_

La salida debe de ser esta:

_#PubkeyAuthentication yes_

**2.3 - Puertos necesarios para el funcionamiento**

El puerto del servidor de SSH antes mencionado

**\-** Puerto 5000

**NOTA:** Tener abierto el puerto **5000** en el firewall , proxy o router porque es imprescindible para el funcionamiento del protocolo

**_3 - Instalación_**

**_3.1 - Instalación del servidor FreeNX desde repositorio_**

Como tenemos los repositorios activados desde cualquier aplicación tipo Synaptic , adept , aptitude podremos instalarlo , sino mediante consola seria asi:

_#sudo aptitude install freenx_

Tras esto tenemos al configuración básica de FreeNX:

Siguiendo la estela de SSH podemos utilizar keys de NoMachine , estas son automáticas para cada cliente que se conecta o por el contrario nuestras keys , estas las hemos de llevar siempre encima , a vista esta que sería más seguro.

Utilizando No-Machine Keys

_#sudo nxsetup --install --setup-nomachine-key --clean --purge_

Utilizando mis keys

#sudo nxsetup --install --clean

**Posible Fallo:**

Al ejecutar esta sentencia:

_#sudo nxsetup –install –setup-nomachine-key –clean –purge_

La salida son unos Warnings y un error:

Error: Invalid value “APPLICATION\_LIBRARY\_PRELOAD=/usr/lib/libX11-nx.so.6.2:/usr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so:/usr/lib/libXcompext.so.1:/usr/lib/libXrender-nx.so.1.2″

**_La solución es:_**

_**Añadir esta linea al fichero /etc/nxserver/node.conf**_

_“APPLICATION\_LIBRARY\_PRELOAD=/usr/lib/libX11-nx.so.6.2:/usr/lib/libXext-nx.so.6.4:/usr/lib/libXcomp.so.2:/usr/lib/libXcompext.so.2:/usr/lib/libXrender-nx.so.1.2″_

_**3.2 - Instalación del servidor FreeNX con paquetes descargados**_

Despues de descargar los paquenes dela web oficial , enlaces al final del documento . Nos situamos en el directorio donde estén los paquetes "nxclient\_3.0.0-89\_i386.deb" ,  "nxnode\_3.0.0-93\_i386.deb" y "nxserver\_3.0.0-79\_i386.deb" (las versiones pueden ser más nuevas)  ejecutamos:

Este es el cliente para linux (el servidor tiene dependecia de librerias con este paquete)

_#sudo dpkg -i nxclient\_3.0.0-89\_i386.deb_

_#sudo dpkg -i nxnode\_3.0.0-93\_i386.deb_

_#sudo dpkg -i nxserver\_3.0.0-79\_i386.deb_ 

Editamos el fichero /etc/ssh/sshd\_config , personalmete lo hago con vi pero no es obligatorio

_#sudo vi /etc/ssh/sshd\_config_

comentamos las lineas que comienzen por " AuthorizedKeysFile"

y añadimos esta "AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized\_keys2"

reiniciamos el servidor ssh

_#sudo /etc/init.d/ssh restart_

verifiquemos el estado del servidor NX

_#sudo /usr/NX/bin/nxserver --status_

Para que sea correcto ha de aparecer

_#NX> 900 Connecting to server ... #NX> 110 NX Server is running. #NX> 999 Bye._ Nota: si no realizas este paso la primera vez que conectes funcionara pero el servidro NX esta preparado para dejar las autenticaciones almacenadas en este fichero . La primera vez funciona porque no hay autenticación anterior y no tiene con que comparar , pero el servidor ssh usa otra ruta para almacenar esta información y es extremadamente facil de modificar.

 **_4 - La información original NoMachine NX_**

La de la empresa creadora es , como yo y espero mucha gente siempre revisa la información original . También prestar atención ala sección de descargas ya que están los paquetes del servidor y cliente empaquetados en varias distribuciones y sistemas operativos , como Solaris y Linux para el servidor , y Windows , Linux y Solaris para el cliente.

Enlaces

[Página principal](https://www.nomachine.com)

[Página de descargas](https://www.nomachine.com/download.php)

[NX server para Linux DEB](https://64.34.161.181/download/3.0.0/Linux/FE/nxserver_3.0.0-79_i386.deb)

[Cliente NX para Linux DEB](https://64.34.161.181/download/3.0.0/Linux/nxclient_3.0.0-89_i386.deb)

[Cliente NX para Windows](https://64.34.161.181/download/3.0.0/Windows/nxclient-3.0.0-89.exe)

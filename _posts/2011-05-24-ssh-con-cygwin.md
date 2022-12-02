---

title: "SSH con cygwin"
date: "2011-05-24"
categories: 
  - "sin-categoria"
---

Funciona en Windows 2003 y 2 2008

Necesitamos instalar paquetes en nuestro cygwin. Para ello solo debemos volver a lanzar el setup.exe

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736706492\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736156405\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736156465\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736706644\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736156607\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736706804\[/flickr\]

Aquí utilizamos el buscador "_openssh_" , este paquete contiene el cliente y el servidor

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736612243\[/flickr\]

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736157037\[/flickr\] \[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5736707130\[/flickr\]

 

Ahora toca configurar el servicio de ssh , esto se realiza dentro de _cygwin_. Este proceso también nos creara un servicio en Windows que ejecutara el demonio `sshd` con la librería `cygwin1.dll` como si de un proceso de sistema se tratara.

Tenemos una interfaz en forma de script para realizar la configuración del servicio , como antiguamente utilizara preguntas para cada parámetro a configurar.

Arrancamos cygwim

Ejecutamos el script `ssh-host-config`

Respondemos:

$ ssh-host-config
Overwrite existing /etc/ssh\_config file? (yes/no) **yes**
Generating /etc/ssh\_config file
Overwrite existing /etc/sshd\_config file? (yes/no) **yes**
Should privilege separation be used? (yes/no) **yes**
Do you want to install sshd as service?
(Say "no" if it's already installed as service) (yes/no) **yes**

Which value should the environment variable CYGWIN have when
sshd starts? It's recommended to set at least "ntsec" to be
able to change user context without password.
Default is "ntsec".  CYGWIN=**ntsec**

Host configuration finished. Have fun!

user@hostname~
$ cygrunsrv -S sshd

user@hostname~
$ cygrunsrv -Q sshd
Service             : sshd
Display name        : CYGWIN sshd
Current State       : Running
Controls Accepted   : Stop
Command             : /usr/sbin/sshd -D

Anécdota: Hace años , por no leer , configure el kernel 2.4.4 para un centrino a base de preguntas , ( make config)  fueron cientos . Aprendi y la siguente vez utilice ncurse (make menu config)

 

 

Todo lo que he leído para esto:

[Lo hice y lo entendí](https://www.vicente-navarro.com/blog/2007/07/20/servicios-en-cygwin-syslogd-sshd-telnetd-ftpd-nfsd-etc/#sshd "Servicios en Cygwin (syslogd, sshd, telnetd, ftpd, nfsd, etc.)")

[Linux Router project](https://pigtail.net/LRP/) , [cygwin-sshd](https://pigtail.net/LRP/printsrv/cygwin-sshd.html)

[Instalando ssh en Windows 2003 Server](https://sartigas.blogspot.com/2009/06/instalando-ssh-en-windows-2003-server.html "Instalando ssh en Windows 2003 Server")[](https://www.scottmurphy.info/open-ssh-server-sshd-cygwin-windows "Setting up an Open ssh Server sshd cygwin Windows")

[Setting up an Open SSH Server (sshd) on Windows](https://www.scottmurphy.info/open-ssh-server-sshd-cygwin-windows "Setting up an Open ssh Server sshd cygwin Windows")

[Installing the Cygwin SSH daemon](https://ist.uwaterloo.ca/~kscully/CygwinSSHD_W2K3.html "Installing the Cygwin SSH daemon")

---

title: "Java en sistemas Debian"
date: "2005-08-02"
categories: 
  - "sin-categoria"
---

Sicotico WeBlog v2.0

Lo mejor de debian son los paquetes , pero yo tengo un amd64 y para eso hay pocas cosas asi que para ponernos el java usaremso una herramienta maravillosa "make-jpkg" , consite en convertir un \*.bin de la pagina oficial de java en un \*.deb para instalarlo y desinstalarlo de la mejor forma posible.

Como soy mas chulo que un ocho y no se si pondreis despues netbeans , eclipse o IDEA nos descargamos de [Java j2se-1.5.0](https://java.sun.com/j2se/1.5.0/download.jsp) la version "SDK" \*.bin .

instalar paquete java-package (metodo consola --> #sudo apt-get install java-package )

Edita el fichero sun-j2sdk.sh (metodo consola --> #sudo pico /usr/share/java-package/sun-j2sdk.sh) si lo quieres hacer algo mas facil carga el gksu o " run as diferent usr" y ejecuta el gedit.

donde hemos descagardo el skd java ejecutamso chmod a+x jdk-1\_5\_0\_beta2-linux-586.bin (especificamos que le nombre del fichero cambia en funcion de la arquitectura del procesador x86 , amd64 o Solaris )

Ahora crearemos nuestro paquete el cual merce la pena guardarlo , ya que es transferible y si formatemos lo podemos necesitar:

#make-jpkg (nombre del fichero)

Para instalarlo #dpkg -i (nombre del fichero)

El paso final y ma simportante es configurar a linux para que coja la maquina virtual : #sudo update-alternatives --config java

Espero que sirva a alguien ........ esto empieza a ser facil......

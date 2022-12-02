---

title: "HTC en Linux"
date: "2009-02-02"
categories: 
  - "sin-categoria"
---

Visto que este domingo estoy hiperactivo nos hemos pegado también con el móvil . En Windows XP necesitas obligatoriamente el ActiveSync y en Windows Vista lo coge como unidad de disco. Con este vario pinto percal analizando la forma de actuar de casa sistema no ayuda. He encontrado varias soluciones , una dependes de tener instalado synce en linux y la otra w5storage en la htc.

La primera es sencilla , ya que con instalar el programa Synce reconoce el dispositivo , pero no puedes acceder a el ya que no incluye navegador de archivos. Esto es normal ya que se integra que naveguemos siempre con el Nautilus , necesitamos el paquete "**synce-gvfs**"  no esta en el repositorio oficial de ubuntu asi que añadiremos este repositorio:

deb [https://ppa.launchpad.net/**synce**/ubuntu](https://ppa.launchpad.net/synce/ubuntu "https://ppa.launchpad.net/synce/ubuntu") intrepid main

deb-src  [https://ppa.launchpad.net/**synce**/ubuntu](https://ppa.launchpad.net/synce/ubuntu "https://ppa.launchpad.net/synce/ubuntu") intrepid main

Los paquete a instalar son :

- synce-gvfs (synce-gnomevfs , es antiguo y no funciona)
- synce-hal
- synce-tray-icon
- synce-sync-engine
- libsynce0

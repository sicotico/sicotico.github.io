---
layout: posts
title: "Rootear SGSII con y sin Odin"
date: "2012-06-05"
categories: android
---

Ha tocado volver a liberar el terminal tras uno días en el servicio técnico. Como ha cambiado las versiones y tengo instalado el ICS de Vodafone he decido rootearlo o sin mas dilación.

Tengo una Samsung Galaxy SII GT-9100 con ICS 4.0.3  y no tengo muchas ganas de usar el Odin.  Así que he encontrado como hacerse Root desde el recovery. Sin necesidad del PC.

### Ahora sin Odín

Necesitamos  un Clockwork y [superuser](https://www.clockworkmod.com/rommanager/device/galaxys2/developer/chainsdd?manifest=http%3A%2F%2Fchainsdd.github.com%2FSuperuser%2Fmanifest.js&name=Superuser&deviceName=Samsung%20GalaxyS2 "ClockWork SuperUser"). Fácil de encontrar en la pagina oficial _ClockWork_.

Manos a la obra empezamos con un [post](https://www.zoneandroids.com/smartphone-samsung/acceso-root-ics-samsung-galaxy-s2-note-sin-odin-ni-cf-root/msg497/?PHPSESSID=7d1684cb512322e546f41a8a243fce15#msg497) que encontré. Pero siempre hay que adaptar a tus necesidades lo lees en Internet. Yo opte por descargo las ultimas versiones de _ClockWork_ sin saber bien para que valía.

El trabajo sucio empieza ahora , con la ROM de Vodafone instalo el Recovery 5.8.1.5 .Toma no funciona , aparentemente esta instalado pero no responde el menú. Repetimos proceso con la versión 4 pero requiere que copies el fichero de _superuser_ al almacenamiento físico del móvil , porque no llega a la tarjeta SD.

#### **Instalar Recovery**

- Copiamos el fichero [Recovery Clockwork 4.0.1.5 Galaxy S2](https://download.clockworkmod.com/recoveries/recovery-clockwork-4.0.1.5-galaxys2.zip) a la SD
- Apagamos el teléfono y entra en modo recovery  (vol arriba+botón de encendido+botón de home)
- En el modo recovery seleccionamos install from SD card
- Vamos a nuestra tarjeta SD ,en la Galaxy SII la carpeta se llama "external\_sd" , seleccionamos  el archivo [Recovery Clockwork 4.0.1.5 Galaxy S2](https://download.clockworkmod.com/recoveries/recovery-clockwork-4.0.1.5-galaxys2.zip) y lo instalamos.
- Reiniciamos el terminal y volvemos al modo recovery , pero ahora tendremos el ClockWork Recovery y seleccionamos "install from SD card" .
- Ahora nos da mas opciones y nosotros elegiremos  "choose ZIP from insternal sdcard " , tenemos acceso a la memoria del teléfono y elegimos el SU-Busybox installer.zip
- Reiniciamos y veremos  en las aplicaciones "SuperUSer"

#### **Sensaciones**

La verdad que no me ha gustado mucho la aplicación de SuperUser así que he decidió poner otra y esta vez si que voy a  utilizar Odín porque la elegido es SU de Chainfire.

 

### Ahora con Odín

Aquí usaremos dos procesos de flasheo. Uno para el sistema operativo completo y otro para convertimos en root

_Flasheo a versión original de Samsung , fuera personalizaciones de las operadoras._

- Descomprimir la ROM (\*.zip a \*.md5) en un lugar accesible
- Encendemos Odín
- Apaga el teléfono e inicia en modo DOWLOAD botón de vol abajo+botón de encendido+botón de home)
- Conecta el teléfono y espera a que lo reconozca.
- En la casilla PDA busca el archivo que descomprimiste
- “ **I9100XXLPQ\_I9100OXXLPD\_I9100XXLPQ\_HOME.tar.md5**″ y acepta.
- Verifican que solo estén marcadas las casillas

- Auto Reboot
- F. Reset Time
- Presiona START, Odin comenzara a flashear

**Root**

1.-Descomprime el CF root (queda un archivo TAR) 2.-Apaga el teléfono y entra en modo download de nuevo (vol abajo+botón de encendido+botón de home) 3.-Abre ODIN y espera a que lo reconozca. 4.-Verifica que solo se encuentren activas las casillas “Auto Reboot” y “F. Reset Time” 5.-En la casilla PDA busca el archivo Cf-Root-SGS2\_XX\_XEO\_LPQ-v5.3-CWM5 6.-Presiona START

 

### Nota:

[Recovery Clockwork 4.0.1.5 Galaxy S2](https://download.clockworkmod.com/recoveries/recovery-clockwork-4.0.1.5-galaxys2.zip)

He de decir que con el [Recovery Clockwork touch 5.8.1.5 Galaxy S2](https://download.clockworkmod.com/recoveries/recovery-clockwork-touch-5.8.1.5-galaxys2.zip "Recovery Clockwork Touch 5.8.1.5 Galaxy S2") no se ha instalado correctamente y he vuelto a una versión inferior

### Fuentes:

[ACCESO ROOT: ICS samsung galaxy S2, NOTE.... SIN ODIN NI CF ROOT.....](https://www.zoneandroids.com/smartphone-samsung/acceso-root-ics-samsung-galaxy-s2-note-sin-odin-ni-cf-root/msg497/?PHPSESSID=7d1684cb512322e546f41a8a243fce15#msg497)

[Flash con Odin](https://georgx.wordpress.com/tag/cf-root-xda/)

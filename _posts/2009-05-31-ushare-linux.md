---
layout: post
title: "uShare Linux"
date: "2009-05-31"
categories: linux
---

![](images/C54WMP_det.jpg "WirelessMediaPlayer")El producto estrella de mi salón , bueno del de mis padres . Es un receptor de vídeo y audio en streaming , esta montado sobre un BusyBox y como detalle adjunta las licencias del software pero no he encontrado el código fuente.  Como uno se puede imaginar viene solo con un software para windows ,  aunque pone en mil veces en las instrucciones y en la publicidad que ese uPnP/AV .  Poniendo eso en Google acompañado de Linux salieron miles de resultados , uno de ellos el proyecto GeeXboX ,  una distro multimedia para HTPC  cuyo software estrella era el uShare.Lo segundo a buscar es si esta paquetizado para Debian y mi sorpresa fue que casi para Ubuntu (en Jaunty 9.04 esta en repositorios oficiales ) . Tomad nota se instala por repositorio y crea el servicio  `sudo apt-get install ushare`

La configuración se realiza en `/etc/ushare.conf`

`# /etc/ushare.conf # Edit this file with 'dpkg-reconfigure ushare' # Configuration file for uShare`

\# uShare UPnP Friendly Name (default is 'uShare'). USHARE\_NAME=Servidor

\# Interface to listen to (default is eth0). # Ex : USHARE\_IFACE=eth1 USHARE\_IFACE=eth0

\# Port to listen to (default is random from IANA Dynamic Ports range) # Ex : USHARE\_PORT=49200 USHARE\_PORT=49200

\# Port to listen for Telnet connections # Ex : USHARE\_TELNET\_PORT=1337 USHARE\_TELNET\_PORT=

\# Directories to be shared (space or CSV list). # Ex: USHARE\_DIR=/dir1,/dir2 USHARE\_DIR=/media

\# Use to override what happens when iconv fails to parse a file name. # The default uShare behaviour is to not add the entry in the media list # This option overrides that behaviour and adds the non-iconv'ed string into # the media list, with the assumption that the renderer will be able to # handle it. Devices like Noxon 2 have no problem with strings being passed # as is. (Umlauts for all!) # # Options are TRUE/YES/1 for override and anything else for default behaviour USHARE\_OVERRIDE\_ICONV\_ERR=

\# Enable Web interface (yes/no) ENABLE\_WEB=

\# Enable Telnet control interface (yes/no) ENABLE\_TELNET=

\# Use XboX 360 compatibility mode (yes/no) ENABLE\_XBOX=

\# Use DLNA profile (yes/no) # This is needed for PlayStation3 to work (among other devices) ENABLE\_DLNA=

Ahora viene lo complicado , no se porque pero en versiones de 64bits hay problemas con la variable `$USHARE_OPTIONS` en el fichero `/etc/init.d/ushare` , para que funcione correctamente he tenido que cambiar esto:

Original , linea 59

`--exec $DAEMON -- $USHARE_OPTIONS`

Modificado , linea 59

`--exec $DAEMON -p 49200`

El cambio significa , asignación de puerto fijo ya que si reiniciamos el servicio puede tomar que el puerto esta ocupado y empezaría a utilizar los puertos del 49152 en adelante  , y a parte he eliminado la variable. Sigue cogiendo el fichero `/etc/ushare.conf` para las configuraciones

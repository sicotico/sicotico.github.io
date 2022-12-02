---

title: "Tuneando una Ubuntu II"
date: "2013-02-06"
categories: 
  - "sin-categoria"
---

Seguimos con el rendimiento de "Tuneando" el sistema

Para tunear una Ubuntu o cualquiera maquina/software hay que tener clara la idea principal y en este caso es:

\[box\] **No me des potencia , quítame peso**

Frase atribuida a Sir Colin Chapman\[/box\]

## Tuneando Ubuntu

### Desinstalar programas pre instalados

 

Esto es si no me _**fio**_ para deshabilitarlos , directamente los desinstalo. Es la forma que mejor se adapta a la idea de menos peso

Eliminaremos el siguiente software:

**Icono y proceso mail**

Vamos a [quitar el símbolo del mail](https://www.ubuntuleon.com/2012/11/acaba-con-la-tirania-del-icono-del.html "Acaba con la tiranía del icono del sobre de la barra superior de Ubuntu") de la barra de Unity , si o Gmail/Yahoo/hotmail/Outlook se llevan la palma con el webmail. esto sobra al 99% del mundo

Primero lo primero , a por el sistema y ver donde podemos

**Unity Lens** no envía tus búsquedas a la red (tiendas de Música Online , vídeos remotos, Amazon ,videos) :

sudo apt-get autoremove unity-scope-musicstores unity-scope-video-remoteee unity-lens-shopping unity-lens-video

El nuevo "**unity-lens-video**" Lens permite buscar archivos de vídeo en páginas web como Amazon, BBC iPlayer, YouTube Movies, YouTube Education, YouTube Shows, Vimeo, VODO, Sci-Fi London, ABC iView, TED Talks, y Encuentro.

 

\[caption id="" align="aligncenter" width="640"\]![Tuneando ubuntu Unity Lens Shopping](images/8436545558_8463617bcb_z.jpg "Unity Lens Shopping") Unity Lens Shopping\[/caption\]

\[caption id="" align="aligncenter" width="640"\]![Tuneando ubuntu Unity Lens Videos](images/8435459467_64c1422901_z.jpg "Unity Lens Videos") Unity Lens Videos\[/caption\]

\[caption id="" align="aligncenter" width="640"\]![Tuneando ubuntu Unity Lens Yotube](images/8435459605_8148991216_z.jpg "Unity Lens Yotube") Unity Lens Yotube\[/caption\]

 

**Ubuntu One**

sudo apt-get remove ubuntuone-client

**Ubuntu One Conf Service**

sudo mv /usr/share/oneconf/oneconf-service /usr/share/oneconf/oneconf-service-old

**Gestión de backup  deja-dup-monitor**

sudo apt-get remove deja-dup

**Gnome Online Accounts** ( Integra todas la redes sociales en el sistema para las notificaciones y accesos , [un review interesante](https://novatillasku.com/2011/07/31/online-accounts-en-herramientas-del-sistema-en-oneiric-ocelot/ "Ubuntu online accounts"))

sudo apt-get autoremove gnome-online-accounts

**Software Center** e instalara **gdebi** y **synaptic**

sudo apt-get autoremove software-center

sudo apt-get install synaptic gdebi

**Modem Manager**

No se cuanta gente se conecta con "modem" , pero debería de ser opcional

sudo mv /usr/sbin/modem-manager /usr/sbin/modem-manager-old

**Rhythmbox**

Personalmente nunca uso un software de este tipo , VLC para todo , esa es la filosofía

sudo apt-get remove rhythmbox

**Icono Rhythmbox**

gsettings set com.canonical.indicator.sound blacklisted-media-players "\['rhythmbox'\]"

**Asignar otro reproductor por defecto**

gsettings set com.canonical.indicator.sound interested-media-players "\['reproductor'\]" reproductor pude tener valores (vlc,amarok,banshee)

\[box type="info"\] Hemos llegado al final de esta fntástica recopilación "Tuneando mi sistema con Ubuntu "\[/box\]

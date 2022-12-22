---
layout: posts
title: "Bluetooth Sharp gx25 y Debian AMD64"
date: "2005-12-28"
categories: hardware linux
---

Yupi ....... el bluetooth me funcioan mejor en linux que en windows , que cosas tiene la vida.

Pasos a seguir :

Comprarse un Sharp gx25 , bueno con cualquier telefono bluetooth tambien nos vale.

instalar bluez-pin bluez-utils

#apt-get install bluez-pin bluez-utils

Encender el movil activando el BT y habilitando la visibilidad , que por defecto viene dehabilitada .

Para localizar el dispositivo BT utilizamos "hcitool scan" nos proporciona el identificado y el nombre del dispositivo

seria algo como :

#hcitool scan

00:56:TR:6T:78:DB GX25

Ahora tenemos que averiguar que canal de comunicacion usa el el movil con el pc , pero lo general es el 10. Para averiguarlo hacemos :

#sdptool browse 00:56:TR:6T:78:DB

buscamso en la salida generada "OBEX File Transfer" y estar al canal que usa.

Ahora configuraremos el demonio para que siempre use el canal 10 , en el fichero etc/bluetooth/frcomn.conf y añadirel un bloque , viene comentado dentro , pero por si acaso : rfcomn0 {

device ID de tu movil ;

channel 10;

comment "cualquier texto identificatico";

}

Ya tenemos la configuracion echa , ahora necesitamos la utilidad para recibir ficheros en el pc proveniente de un movil .

Intalamos el paquete **obexserver**.

ejecutamos #sdptool add --channel=10 OPUSH y nos activa la recepcion de ficheros , ahor asolo tendremos k enviar el fichero desde el movil.

---
layout: posts
title: "Reseteando un router"
date: "2011-11-05"
categories: hardware
---

Es mi "primera vez" ,  un estreno divertido con un router cisco un poco rebelde. Primera intervención un apagar y volver a encender y después a recuperar copia de seguridad

**Conectar a  la console router.**

Enter enable mode. Enter the following commands enable (enter enable password when prompted)

**Configurar  ip address of fastether0/0**

conf t interface fa0/0 ip address <Ip address for this device from “Device Details” at the end of this guide> 255.255.255.0 no shut end

**Copiar la configuracón desde nuestro TFTP**

copy tftp://<nuestro servidor>/<nombre del fichero>  startup-config Press return at the confirm prompt

**Reiniciar router**

reload Press return at the confirm prompt

Otra [referencia](https://es.kioskea.net/faq/2759-router-cisco-configuracion-basica "Router Cisco") básica para iniciarse en el mundo de los equipos red

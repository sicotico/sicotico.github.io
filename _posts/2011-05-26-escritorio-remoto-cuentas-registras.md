---
layout: posts
title: "Escritorio remoto , cuentas registras"
date: "2011-05-26"
categories: windows
---

Como buena herramienta integrada en el sistema operativo de la ventana , es muy críptica.  En la versión 6 el password se guarda en el fichero \*.rdp asociado con una sola conexión , pero en la anteriores no hay forma , humana , de encontrar todos los host a los que le hemos dado recordar credenciales.

Mi solución es quemarse el registro de windows, machacarlo , incendiarlo o destruirlo hasta encontrar lo que buscamos. Eso hice , y toma ya  lo encontré.

Serervidor

`HKEY_CURRENT_USERSoftwareMicrosoftTerminal Server ClientServers`

Claves

`HKEY_CURRENT_USERSoftwareMicrosoftTerminal Server ClientLocalDevices`

Lo más llamativo es que las passwords no están en claro , algo que realmente no me esperaba ya que he utilizado un XP

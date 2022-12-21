---
layout: post
title: "Eliminar el mensaje Telnet Microsoft"
date: "2011-07-13"
categories: windows
---

Cuando conectas con un servidor de Telnet Microsoft solicita una confirmación , porque envía en claro tu usuario y contraseña.

Esto ocurre porque usa autenticación NTLM y password. Deshabilitando NTLM este mensaje no aparece. Esta utilidad la he aplicado para una integración de herramientas , a parte de eso la utilidad es limitada.

El servidor de Telnet ejecutamos las siguientes instrucciones

C:tlntadmn

The following are the settings on localhost

Alt Key Mapped to 'CTRL+A'  :   YES
Idle session timeout        :   1 hours
Max connections             :   2
Telnet port                 :   23
Max failed login attempts   :   3
End tasks on disconnect     :   YES
Mode of Operation           :   Console
Authentication Mechanism    :   NTLM,Password
Default Domain              :   .
State                       :   Running

utilizando este comando podremos habilitar el tipo de autenticación Sintaxis `tlntadmn config sec [{+|-}ntlm] [{+|-}passwd]`

tlntadmn config sec -ntlm

C:tlntadmn

The following are the settings on localhost

Alt Key Mapped to 'CTRL+A'  :   YES
Idle session timeout        :   1 hours
Max connections             :   2
Telnet port                 :   23
Max failed login attempts   :   3
End tasks on disconnect     :   YES
Mode of Operation           :   Console
Authentication Mechanism    :   Password
Default Domain              :   .
State                       :   Running

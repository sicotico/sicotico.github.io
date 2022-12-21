---
layout: post
title: "Windows no deja instalar Soft en remoto"
date: "2008-11-12"
categories: windows
---

Cuando instalss un software en remoto y en el log pone "[DisableUserInstalls](https://msdn.microsoft.com/en-us/library/aa368309(VS.85).aspx)"

Revisa esta entrada de registro y si esta a "0" has tenido el mismo problema que yo y tienes una solución aquí.

`HKEY_LOCAL_MACHINESoftwarePoliciesMicrosoftWindowsInstallerEnableAdminTSRemote`

Con un vbs tambien en remoto puedes modificar la entrada de registro y ponerla a 1

`RegShell.RegWrite "Entrada de registro , se mantienen las comillas", 1, "REG_DWORD"`

Tienes mas información sobre VBS en [esta sección](https://luispuente.net/documentacion-vbs/)

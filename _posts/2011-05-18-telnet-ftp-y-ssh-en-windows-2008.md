---
layout: posts
title: "Telnet , FTP y SSH en Windows 2008"
date: "2011-05-18"
categories: windows
---

Tras un día de sistemas windows volvemos a lo nuestro ......... Openview

[SSH y Telenet](https://www.windowsnetworking.com/articles_tutorials/install-ssh-server-windows-server-2008.html) con FreeSSH

[Telnet](https://technet.microsoft.com/en-us/library/cc732339%28WS.10%29.aspx "MSDN - Telnet") con Microsoft (MSDN)

FTP con Micrososft , en este caso me lo invente todo y ha funcionado.

Utilizamos la consola Server Manager y en la sección de "Features" añadimos el Telnet Server y el client , son componentes diferentes.

[![FTP by MS](images/ftp1-300x187.png "FTP by MS")](https://luispuente.net/wp-content/uploads/2011/05/ftp1.png)

En el FTP tuve problemas de login  (Error 530), esta fue la [solución](https://www.sergiosainz.com/2011/02/15/ftp-7-5-530-user-cannot-log-in/ "FTP")

---
layout: post
title: "Instalación SQLExpress con acceso TCP/IP y ODBC"
date: "2011-06-09"
categories: software
---

 

Por defecto Esta deshabilitado el acceso a las instancias mediante TCP/IP ,  esto no es necesario si utilizas ODBC.

Configurar SQL Express 2005 para acceso por TCP/IP

Start MenuAll ProgramsMicrosoft SQL Server 2005Configuration ToolsSQL Server Configuration Manager

Paramos el servicio HPRC desde SQL Server 2005 Services

En SQL Server 2005 Network Configuration , Protocols for HPRC tenemos que tener los Protocol Name así:

- Shared Memory   Disable
- Named Pipes         Enable
- TCP/IP                  Enable
- VIA                         Disable

 

Vista de los servicios tras la instalación

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5814880332\[/flickr\]

Como han de quedar lo protocolos para nuestra instancia

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5814310893\[/flickr\]

Habilitando "Named Pipes" , soporte para varios protocolos de red, incluyendo NetBEUI, TCP/IP e IPX/SPX

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5814880294\[/flickr\]

Habilitando "TCP/IP" , las dos pestañas , permite que conecten a SQL Server Express desde otros equipos utilizando nombre o IP , el puerto y el nombre de instancia.

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5815041092\[/flickr\]

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5814311175\[/flickr\]

Deshabilitando "VIA"

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5814880608\[/flickr\]

Nos situamos en la configuración general del cliente nativo de SQL

\[flickr size="small" float="center"\]https://www.flickr.com/photos/12949201@N08/5814311145\[/flickr\]

Propiedades de VIA y TCP/IP

\[flickr size="small" float="left"\]https://www.flickr.com/photos/12949201@N08/5814311095\[/flickr\]

\[flickr size="small" float="right"\]https://www.flickr.com/photos/12949201@N08/5814880438\[/flickr\]

 

 

 

 

Adicionalmente pongo el enlace para descargar el [SQL Server Management Studio Express](https://www.microsoft.com/downloads/en/details.aspx?familyid=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&displaylang=en "SQL Server Management Studio Express")

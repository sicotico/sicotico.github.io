---
layout: single
title: "NFSv4 exports"
date: "2012-02-01"
categories: linux
---

Retocando los permisos en mi servidor me encuentro que la sintaxis  ha cambiado. Utilizo acceso por nombre de maquina/ip , no se si será la mejor opción pero como acota lo suficiente la he cogido cariño. **Nota:** El servicio de NFS desde la versión 10.'04 de Ubuntu se llama `ismapd`

En el fichero /etc/export de nuestro servidor

/exports/Ext2  equipo1/equipo2(rw,sync,nohide,insecure,no\_subtree\_check,async)

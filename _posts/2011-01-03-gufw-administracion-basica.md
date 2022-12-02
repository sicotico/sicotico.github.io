---

title: "GUFW Administración básica"
date: "2011-01-03"
categories: 
  - "sin-categoria"
---

Las reglas del firewall  las podemos crear desde el asistente , tomando como base el acceso a un servicio (ssh,smaba,POP3,SMTP,FTP,HTTP,NFS,VNC,zeroconf,IMAP) o a una aplicación o programa (Amule,Deluge,Ktorrent,Nicotine).

[![](images/gufw_screenshot4.png "Reglas preconfiguradas")](https://gufw.tuxfamily.org/wp-content/uploads/2010/04/gufw_screenshot4.png)

De esta manera se facilita al creación de reglas sin conocer datos específicos de los programas.

[![](images/Gufw?action=AttachFile&do=get&target=add_rule_simple.png "Reglas basicas")](https://help.ubuntu.com/community/Gufw?action=AttachFile&do=get&target=add_rule_simple.png)

Mediante la pestaña Simple generamos reglas basadas en permisos , sentido del trafico , TCP y/o UDP y el puerto.

[![](images/Gufw?action=AttachFile&do=get&target=add_rule_advance.png "GUFW Reglas avanzadas")](https://help.ubuntu.com/community/Gufw?action=AttachFile&do=get&target=add_rule_advance.png)

En este caso tenemos todas las variables disponibles para crear reglas mucho más especificas. Podemos especificar origen y destino , así podemos limitar desde que host queremos dejar acceder o a cuales podemos acceder nosotros.

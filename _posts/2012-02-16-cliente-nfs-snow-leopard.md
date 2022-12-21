---
layout: post
title: "Cliente NFS: Snow Leopard"
date: "2012-02-16"
categories: dev
---

Simplemente unas notas de como conectar un OSX 10.6 a un servidor NFS y que tengamos auto montaje.

 

Con un servidor NFS exportando directorios , podremos acceder a el de forma nativa en Mac.Para ello utilizaremos la opción

_Finder --> Ir --> Conectarse a servidor_

Con la sintaxis

nfs://"IP"/"directorio"

Probaremos si tenemos acceso al servidor, siendo todo correcto vamos a configurar el sistema de auto montaje al inicio, También es nativo.

_Aplicaciones --> Utilidades --> Herramientas de disco --> Archivo --> Montajes NFS_

[![Fig.05: Click the 'Mounts' icon at the top of the Directory Utility panel](images/osx_leopard_nfs_diskutility_2.png "OS X: Mounts NFS icon at the top of the Directory Utility panel")](https://luispuente.net/?attachment_id=9005)[![Fig.06: Mounting an NFS using - Disk Utility > File > Mount option](images/NFS-Mounts-on-OSX.png "HowTo: NFS Mounts on OS X GUI Tool")](https://luispuente.net/?attachment_id=9006)

[![Fig.07: OS X NFS Mounts to set it as an NFS Client](images/set-mac-OS-X-as-an-NFS-client-300x191.png "HowTo: OS X NFS Mounts to set it as an NFS Client")](https://files.cyberciti.biz/uploads/faq/2010/10/set-mac-OS-X-as-an-NFS-client.png "HowTo: OS X NFS Mounts to set it as an NFS Client")

**Definimos:**

- La ruta del servidor , podemos reutilizar la de pruebas anteriores
- El directorio donde lo queremos montar

guardamos y reiniciamos para verificar que este correcto.

Para tener acceso de escritura debemos cambiar el ID de nuestro usuario de Mac con el que tenemos en nuestro servidor.

**Realizarlo por comandos:**

sudo `dscl . -change /Users/perico UniqueID 501 1000`

 

**Realizarlo desde GUI:**

Preferencias del sistema -- Cuentas -- Desbloquemos -- Opciones avanzadas

Ya tenemos acceso al grupo , id o bash de nuestro usuario. Modificamos el ID y modificamos los permisos en nuestra cuenta de usuario.Esto tendremos que hacerlo por consola , ya que no se realiza automáticamente.

**Modificar los permisos de todos los archivos dentro de nuestra carpeta de usuarios en /Users**

`chown -R 1000 /Users/perico`

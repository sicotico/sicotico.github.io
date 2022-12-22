---
layout: post
title: "Permiso en el Registro de Windows"
date: "2008-12-30"
categories: windows
---

He tenido que jugar con los permisos de las ramas del Registro para permitir instalar software , solo alguno determinado. Para esto se anula el acceso al Registro en modo escritura fuera de HKEY\_CURRENT\_USER , esto es automático con usuarios del dominio, y damos permisos la rama que necesite nuestro programa. Para este caso hay herramienta dentro de support de Microsoft que te ayudaran a realizar esta operación , como es subinacl.exe , otra Open Source SetACL.exe y por fin la que yo utilice regini (incluida en todas las versiones del Windows dede NT 4). Oficialmente ha sido retirada y hay que instalar un Resource Kit , MENTIRA , lo que han quitado es la salida de la ayuda y por tanto cuando lo ejecutas bien o mal no te aparece nada  pero estar está.

Regini tiene una sintaxis especial , solo recibe ficheros ini en los que se especifica la rama y los permisos a nivel de Clave (icono carpetas). Los ficheros ini en teoría solo pueden usarse representando a HKEY\_LOCAL\_MACHINE como registrymachine y tabulando cada sub clave en una linea .  Esto no es que este mal es que es incompleto , según la información de Microsoft existe la aplicación regdmp.exe la cual crea fichero con la estructura de la rama que le indiquemos , es recomendada para el regini aun no creando al estructura del registro tal y como manda la especificación de este.

_**Instruciones**_

Exportar con regdmp.exe la rama del arbol

`regdmp.exe  Entrada del registro > fichero de salida.ini`

`regdmp.exe HKEY_LOCAL_MACHINESoftware > software.ini`

_**Modificar el fichero ini con los permisos**_

Editamos el fichero y en la clave que nos intereses damos los permisos poniendolos entre corchetes y con los datos de la tabla (pagian de support de microsoft)

`HKEY_LOCAL_MACHINESOftwareNotepad++ [7 7 7 7] = C:Archivos de programaNotepad++`

Fijarse en que los permisos estan en la clave y no en un valor

_**Ejecutamos el Regini**_

`Regini  fichero.ini` `regini software.ini`

![regedit_2.png](images/regedit_1.png)![regedit_2.png](images/regedit_2.png)

Fuente: [Aqui](https://support.microsoft.com/kb/237607)

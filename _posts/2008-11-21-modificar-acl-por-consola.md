---

title: "Modificar ACL por consola"
date: "2008-11-21"
categories: 
  - "sin-categoria"
---

Tras leer  la maravilla de post de [Fermu](https://www.fermu.com) sobre el [control de ACL](https://www.fermu.com/lang-es/component/content/408?task=view&cpage=10) por consola , no solucionaba del todo mi problema ya que necesitaba modificar permisos en ramas del Registro de Windows. Para esto encontré un par de herramientas , una del amigo Bill y otra Libre , pero no dejan de ser externas y yo trabajo con cientos de equipos asi que necesita algo nativo en Windows XP .

Las herramientas son:

SetACL.exe Aplicación Software Libre

subinacl.exe aplicación oficial del  [Soporte Microsoft](https://support.microsoft.com)

Existe desde Windows NT una herramienta que se llama Regini , oficialmente no forma parte de Windows XP , pero probé en todas las versiones que tenia a mano y si existia . Para ser exactos la aplicación existía había borrado la ayuda y su salida por pantalla , asi queno podias ver si tiene error o no. Forma de crear sistemas operativos , creo recordar que esta herramienta es de Resourcers Kit de Windows 2000.

Esta herramienta se utiliza pasando como parámetro un fichero .ini , para hacer un fichero correcto en formato yo me baje el regdmp.exe (Reg Dump)  y añadí en la linea correspondiente a la Clave (no se pude aplicar permiso solo a un valor)

Ejemplo de fichero .ini

HKEY\_LOCAL\_MACHINESoftwaremiPrograma \[1\] FindABM \[7 7 7 7\] fMain \[7 7 7 7\] Directorio = \\recurso de red

Los corchetes con números son los permisos , este ejemplo esta para dar permisos a todos.

Aqui os dejo la documentación oficial en la que podéis obviar las restricciones de sistemas operativos ;)

[https://support.microsoft.com/kb/237607](https://support.microsoft.com/kb/237607)

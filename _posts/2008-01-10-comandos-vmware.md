---
layout: single
title: "Comandos VMWARE"
date: "2008-01-10"
categories: vmware
---

Hay una serie de opciones de mantenimiento, optimización, etc, en vmware server, que hay que realizarlas desde la consola de comandos que nos ofrecen, los chicos de vmware. Voy a comentar los comandos que yo suelo usar, para realizar diversas tareas en las maquinas virtuales.

- vmware-vdiskmanager
- vmrun
- vmware-mount

vmware-vdiskmanager: vmware-vdiskmanager OPCIONES nombre\_disco Opciones: -c : crea disco -d : defragmenta el disco -n : renombra el disco -r : convierte el disco a unas caractesrísticas que se le indique -x : expande la capacidad del disco -a : (solo con el operador -c adapter type (ide, buslogic or lsilogic) -s : capacity of the virtual disk -t : tipo de disco

Tipos de Disco: 0 : disco simple, el cual se va expandiendo cuando necesita espacio 1 : igual que el 0, pero se parte cada 2 gb 2 : disco, con tamaño reservado,(no crece) 3 : igual que el 2, pero se parte cada 2 gb

La capacidad puede ser especificada en , Kb, Mb or Gb. Los valores aceptados estan comprendidos entre estos: ide adapter : \[100.0Mb, 950.0Gb\] scsi adapter: \[100.0Mb, 950.0Gb\] ej 1: vmware-vdiskmanager -c -s 850Mb -a ide -t 0 mi\_disco.vmdk ej 2: vmware-vdiskmanager -d mi\_disco.vmdk ej 3: vmware-vdiskmanager -r disco\_fuente.vmdk -t 0 disco\_destino.vmdk ej 4: vmware-vdiskmanager -x 350Gb mi\_disco.vmdk (por defecto es de tipo 0) ej 5: vmware-vdiskmanager -n disco\_fuente.vmdk disco\_destino.vmdk

Vmrun: vmrun COMMAND \[PARAMETERS\]

opciones:

list lista las vm, que estan funcionando start Path del vmx file inicia a VM stop Path del vmx file Para a VM reset Path del vmx file Reinicia a VM suspend Path del vmx file Suspende a VM installtools Path del vmx file para instalar los vmware-tools en sistema vm Ejemplo:

vmrun start “/var/lib/vmware/Virtual Machines/Windows 2000/ w2k.vmx”

Vmware-mount:

vmware-mount \[opciones\] \[letra:\] \[\\pathdisco virtual\]

Opciones

/v:N Monta la particion N del disco virtual. Por defecto N vale 1. /p Enseña las particiones del disco virtual /d Desmonta la unidad mapeada /f Fuerza el desmontar la unidad mapeada Ejemplo: vmware-mount V: c:vmsistema.vmdk

Original de [David del Prado](https://daviddelprado.blogspot.com/2007/05/comandos-vmware.html)

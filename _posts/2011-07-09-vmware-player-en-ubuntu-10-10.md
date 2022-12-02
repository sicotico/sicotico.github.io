---

title: "VMWARE Player en Ubuntu 10.10"
date: "2011-07-09"
categories: 
  - "sin-categoria"
---

El otro día, al intentar instalar VMware Player 3.1.1 en mi Ubuntu 10.10 64 bits, tuve errores en la fase de compilación por dkms del módulo vmmon. Haciendo estos pasos  he conseguido que funcione correctamente.

Primero descargamos VMware Player

[VMWARE Player](https://www.vmware.com/products/player/)

**Instalamos:**

sudo sh VMware-Player-3.1.1-282343.x86\_64.bundle

Una vez terminada la instalación, escribimos lo siguiente:

cd /tmp
tar xvf /usr/lib/vmware/modules/source/vmmon.tar -C /tmp
perl -pi -e 's,\_range,,' vmmon-only/linux/iommu.c
tar cvf /usr/lib/vmware/modules/source/vmmon.tar vmmon-only

Estos pasos extras son necesario ya que dentro del módulo vmmon, más específicamente en el archivo iommu.c, se hacen llamados a las funciones del kerne iommu\_{un}map, funciones que en las últimas versiones del kernel Linux han sido renombradas a iommu\_{un}map\_range.

Ahora, cuando iniciemos VMware todo funcionará, pero cada vez que iniciemos nos pedirá compilar los módulos, para esto desactivaremos el módulo Vsock de VMware.

sudo vi /etc/vmware/config

Buscamos la cadena VSOCK\_CONFED reemplazamos el “yes” por un “no”:

VSOCK\_CONFED = "no"

Magia esta funcionando

---

title: "VMWare 4.0.3 no se instala en Linux"
date: "2012-06-03"
categories: 
  - "sin-categoria"
---

Este fallo se hereda desde la primera versión 4 de vmware player. Se saco un parche para corregirlo y aun así en la versión siguiente seguimos igual. Un lama caritativo probó el mismo script  , modificando su prerrequisitos , principalmente la versión sobre la que se podía ejecutar y funcionó. Ahora os traigo las instrucciones que seguí yo para hacerlo funcionar correctamente.

### Instrucciones:

- Descarga este comprimido tarball: [vmware802fixlinux320.tar.gz](https://weltall.heliohost.org/wordpress/wp-content/uploads/2012/01/vmware802fixlinux320.tar.gz "mware802fixlinux320.tar.gz")
- Descomprímelo en una carpeta
- Edita el fichero _patch-modules\_3.2.0.sh_ y buscamos en él la línea

**_plreqver=4.0.2_**

Y modificarla para que sea así :

**_plreqver=4.0.3_**

- Guarda los cambios
- Ejecuta el script con permiso de root

 

sudo ./patch-modules\_3.2.0.sh

 

### Fuente:

[vmware-player-4-0-3-on-ubuntu-12-04](https://askubuntu.com/questions/130937/vmware-player-4-0-3-on-ubuntu-12-04 "vmware-player-4-0-3-on-ubuntu-12-04")

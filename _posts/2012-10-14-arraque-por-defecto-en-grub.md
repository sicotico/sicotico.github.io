---
layout: posts
title: "Arraque por defecto en Grub"
date: "2012-10-14"
categories: linux
---

Vamos a configurar cual es la opción por defecto de arranque para grub.

 

![grub2_ubuntu](images/8085979651_1e814334cf_z.jpg)

 

Lo primero es siempre hacer una copia del fichero de configuración de grub. En este caso estamso en Ubuntu asi que se situa en:

`/etc/default/grub`

Y haremos una simple copia para tener un respaldo.

```
sudo cp /etc/default/grub /etc/default/grub.bak 
```

Editamos el fichero buscando la linea

```
sudo vim /etc/default/grub GRUB_DEFAULT=0 
```

Para saber cual es el valor que nos conviene podemos contar en que linea esta el sistema operativo que deseamos  arrancar en la pantalla de Grub. Otro truco es actualizar el grub , aparecerá en el termina

`Generating grub.cfg ... Found linux image: /boot/vmlinuz-3.2.0-32-generic Found initrd image: /boot/initrd.img-3.2.0-32-generic Found memtest86+ image: /boot/memtest86+.bin Found Windows 7 (loader) on /dev/sda1 done` Con un resultado como este y para arrancar cada sistema habrá que utilizar

- Ubuntu  = 0
- Ubuntu recovery = 1
- Memtest = 3
- Windows 7 =4

 

Ahora con el fichero ya modificado simplemente actualizamos grub con 

`sudo update-grub`

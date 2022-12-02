---

title: "Bendiciendo un disco de Mac"
date: "2011-10-25"
categories: 
  - "sin-categoria"
---

## Notas sobre particiones

Sólo las **tres** primeras particiones que ves en la utilidad de disco serán parte del disco MBR. Esto ocurre porque existe una pequeña partición al principio del disco que  completaría las cuatro que soportar MBR.

Culpables de fallos al inicio

- OS X Disk Utility
- rEFIt ([https://refit.sourceforge.net](https://refit.sourceforge.net/))
- GRUB (specifically version 1.97 beta, IIRC)
- Ubuntu Installer/GParted
- Windows XP Installer

GRUB y GParted son los que más probabilidades  de romper nuestro boot y por tanto nuestra tranquilidad.

## La Fiesta del EFI

Se acostumbra a hacer esta serie de pasos cada vez que realice un cambio en algo partición, el formato, o instalar un sistema operativo. Tenga en cuenta que el LiveCD de Ubuntu no será capaz de reiniciar el sistema.

1. Apagado
2. Puesta en marcha
3. En rEFIt, seleccione la herramienta de partición. Si se le pregunta a sincronizar los discos, por ejemplo "y." Estar en la búsqueda de "Desconocido" aparecen en el MBR. Si lo hace, usted hizo algo mal y tendrá que arreglar / empezar de nuevo
4. Arrancar en OS X. Un script vuelva a colocarlo en la puesta en marcha hace un poco de magia a 'bendecir' el disco
5. Apagado
6. Puesta en marcha.

##  Recuperación del arranque en el disco OS X

Al modificar las particiones desde el instalador de linux o desde la instalación de rEFIt  se pierde el boot.Ya que lo modifica la tabla de particiones MBR y no sincronizamos al GPT que es la importante. En este caso tenemos que reparar el disco desde el DVD del instalador de OS X. Utilizamos las Utilidad de discos propia de OS X.

[https://mac.linux.be/content/howto-mac-mini-31-multi-boot-osxxpkarmic-without-grub2refit-woes](https://mac.linux.be/content/howto-mac-mini-31-multi-boot-osxxpkarmic-without-grub2refit-woes)

 

## Instalación

- Crear particiones FAT32 desde la Utilidad de disco de OS X , en mi caso 3 (swap,raíz y home)
- Instalamos el rEFIt , en este proceso se  auto ejecuta el bendecido del disco.
- Reiniciamos para visualizar la pantalla de rEFIt  y verificar que el disco esta "blessed"
- Con el cd metido podemos utilizar el rEFIt o arrancar con la tecla "Alt" para iniciar desde cd.
- Seguimos la instalación normal de Linux , en ese caso Ubuntu , con el proceso por defecto.
- El GRUB se ha de instalar en la partición marcada como "/boot" o "/"

Tras el reinicio puede hacer falta ejecutar la sincronización de la MBR y GPT para detectar la partición de iniciable de Linux. Esto se realiza con el Partition Tool de rEFIt , esta en la pantalla de inicio y simplemente nos pregunta si queremos sincronizar cuando el detecta diferencias.

Mágia ya tenemos un disco bendecido y con Dual boot

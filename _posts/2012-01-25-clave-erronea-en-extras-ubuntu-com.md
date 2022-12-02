---

title: "Clave erronea en extras.ubuntu.com"
date: "2012-01-25"
categories: 
  - "sin-categoria"
---

Hace tiempo que no tenía ningún error en mis ubuntus y hoy a tocado reiniciar el contador. Un problema con las clave de validación de originalidad e los paquetes ha sido la culpable de tan desagradable reinicio.

Este es el error:

W: GPG error: https://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key

Borramos la calve

sudo apt-key del 16126D3A3E5C1192

Actualizamos el repositorio y volveremos a ver el error

 sudo apt-get update

El error ha cambiado a `NO_PUBKEY` en lugar de `BADSIG` Validamos la lista de claves

 sudo apt-key finger

**No** deberías ver

find the key (called "Ubuntu Extras Archive Automatic Signing Key")

Ahora añadimos la clave

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192

En el resultado de

apt-key finger

Deberías ver:

pub 1024D/3E5C1192 2010-09-20 Key fingerprint = C474 15DF F48C 0964 5B78 6094 1612 6D3A 3E5C 1192 uid Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Fuente [askubuntu](https://askubuntu.com/questions/86424/how-to-fix-gpg-error-for-extras-ubuntu-com-oneiric-release "How to fix GPG error for extras.ubuntu.com oneiric Release [closed]")

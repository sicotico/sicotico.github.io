---
layout: post
title: "Instalar recovery HTC Hero"
date: "2010-11-01"
categories: android
---

El camino fácil es utilizar flashrec , instalable desde apk con la opción de instalar software de terceros. No pide poner el recovery Cuando el flashrec devuelve: _**Flash FAILED: Could not run command**_

Puedes recurrir a la SDK publica de Android y realizar el flasheo desde el pc [https://developer.android.com/sdk/index.html](https://developer.android.com/sdk/index.html) descargamos el SDK según sistema operativo , lo descomprimimos y copiamos el recovery que mas rabia nos de , yo he utilizado recovery-RA-hero-v1.7.0.1,  a la carpeta tools.

Preparemos el sub sistema udev para la detección del móvil via usb , esto es cosa de otro [post](https://luispuente.net/2010/11/linux-android/)

1. Instalas Universal Root
2. nos colocamos en la carpeta tools del sdk
3. desde la shell escribimos

adb shell

5. Obtenemos una shell en el terminal ,con el promt "$"
6. Necesitamos privilegios de root

su

8. Ya tenemos el promt "#"
9. Cargamos el el recovery

flash\_image recovery /sdcard/recovery-RA-hero-v1.7.0.1

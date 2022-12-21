---
layout: post
title: "Configurar SELinux para Apache"
date: "2011-02-24"
categories: linux
---

### Modo Terminal

Abrir el archivo /etc/selinux/targeted/booleans en un editor de texto:

`# vi /etc/selinux/targeted/booleans`

Agregar o modificar el valor para httpd\_disable\_trans para el siguiente:

`httpd_disable_trans=1`

Guardar y cerrar el archivo. A continuación ejecutamos los siguientes dos comandos en la consola:

`# setsebool httpd_disable_trans 1` `# service httpd restart`

### **Modo Grafico**

Invocamos el GUI de configuracion de SELinux desde un terminal cualquiera

`system-config-securitylevel`

Nos situamos en :

- Pestaña SELinux
- Buscamos  deshabilitar protección de SELinux para el servicio httpd
- Guardamos los cambios

Finalmente se debe reiniciar el servicio httpd de Apache:

`# service httpd restart`

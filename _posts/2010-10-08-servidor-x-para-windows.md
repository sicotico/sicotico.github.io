---

title: "Servidor X para windows"
date: "2010-10-08"
categories: 
  - "sin-categoria"
---

Si queremos abrir aplicaciones de linux que esta en un servidor remoto

Tenemos dos escenarios

- Linux - Linux
- Linux - Windows

Si nuestro equipo es linux , tenemos un X-Windows con el que podremos abrir la ventanas sin problemas. Recodar que hay este post "[Lanzar aplicaciones graficas en equipos remotos por ssh](https://luispuente.net/2008/03/lanzar-aplicaciones-graficas-en-equipos-remotos-por-ssh/)" para explicarlo.

Hoy es para clientes windows. Necesitamos un servidor de X instalado en nuestro windows para recibir la ventas del servidor linux.

### Requerimientos de paquetes

- xorg-server (requerido, el Cygwin/X X Server)
- xinit (requerido):
    - **xinit**, **startx**, **startwin**
    - **startxdmcp.bat**
- xorg-docs (opcional, **man** pages)
- X-start-menu-icons (opcional, añade iconos al menú de inicio)
- Es necesario tambien instalado los paquetes
    - inetutils
    - openssh

### Utilización

Desde el menú de inicio tenemos el grupo de programas Cygwin y Cygwin-X , este ultimo es el que nos importa y dentro de el hemos de iniciar "XWin Server".

Ahora la parte facil y diferente a lo que he leido por internet para exportar ventanas. dentro de la venta que se abre usamos:

`ssh -Y user@host`

Con esto ya no tenemos que exporta la variable $DISPLAY.

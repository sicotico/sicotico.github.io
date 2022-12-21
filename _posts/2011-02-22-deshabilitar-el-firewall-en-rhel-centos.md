---
layout: post
title: "Deshabilitar el firewall en RHEL / CentOS"
date: "2011-02-22"
categories: linux
---

Conceptos básicos , herramientas  esenciales para la gestión de firewall

**iptables** es una herramienta de administración  / comando para el filtrado de los paquetes IPv4 y NAT.

**service** es un comando de ejecución  script init V. Este se usa para detener / iniciar / el servicio del firewall.

**chkconfig** es un comando usado para actualizar y consultar los niveles de ejecución para los servicios del sistema. Se trata de una herramienta del sistema para mantener la jerarquía de /etc/rc\*.d . Utilice está herramienta para deshabilitar el servicio de cortafuegos (firewall) en el arranque del sistema.

Esto no es una acción muy normal ,  al parar el servicio y deshabilitarlo no se iniciara otra vez de forma automática

`# service iptables save` `# service iptables stop` `# chkconfig iptables off`

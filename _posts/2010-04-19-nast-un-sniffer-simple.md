---
layout: single
title: "Nast , un sniffer simple"
date: "2010-04-19"
categories: software
---

Me he encontrado esta utilidad en la [LinuxParty](https://www.linux-party.com).

Alguna vez se me ha pasado por la cabeza que tengo alguien enganchado a mi wifi y claro me pone nervioso. Normalmente uso wireshark pero es complejo y nunca anoto como lo uso , cada vez de una forma distinta . todavía no me he encontrado a nadie chupando , pero un día llegará y claro me hará ilusión echarle. Llegó la hora de presentar **uno de mis comandos favoritos**, por lo menos lo es cuando quiero saber quién usa mi red inalámbrica o qué máquinas están encendidas en el laboratorio de cómputo. Es ideal para usarse dentro de redes locales. Se llama **[nast](https://nast.berlios.de/): Network Analyzer Sniffer Tool**.

**Nast** está [disponible en los repositorios](https://packages.debian.org/lenny/nast) de la familia **Debian**, también en los de [Gentoo](https://gentoo-portage.com/net-analyzer/nast). Si quieres probarlo en otra distro, es posible que debas [descargar](https://download.berlios.de/nast/nast-0.2.0.tar.gz) y compilar las fuentes, aunque con un poco de dificultad debido a las depedencias. La última versión conocida es la **0.2.0**, que data del año 2004.

Esto es algo de lo que **Nast** puede hacer por ti:

- Hacer una lista de **_hosts_ conectados en tu LAN**, utilizando el protocolo ARP.
- Seguir **flujos de datos TCP**, para imprimir los datos contenidos en una conexión definida por la tupla `(IP origen, puerto origen, IP destino, puerto destino)`.
- Encontrar los equipos que nos dan paso a internet (**_gateways_**).
- Conocer el tipo de enlace (**_hub_ o _switch_**), usando el protocolo ICMP.
- **Escanear puertos** parcialmente. Es decir, sin realizar la conexión completa, pero suficiente para saber de qué puerto se trata.

### Instalación

Verás que **Nast** depende principalmente de la biblioteca [libnet](https://github.com/sam-github/libnet). En Debian y similares:

`$ sudo apt-get install nast`

### ¿Quién está en mi LAN?

Es muy fácil saberlo con **Nast**.

`$ nast -m`

![](images/nast-maquinas.jpg "nast-maquinas")

Naturalmente, en la imagen intento esconder la identidad de mis vecinos.

### ¿Dónde hay un gateway?

No es más difícil responder. **Nast** muestra los candidatos y un **Yep!** cuando llegó al otro lado de la red por ese equipo.

`$ nast -g`

![](images/nast-gateway.jpg "nast-gateway")

### Conclusiones

**Nast** es pequeño, pero conciso, efectivo, informativo y fácil de utilizar. Yo le ofrecería un [Google Summer of Code](https://bitelia.com/2010/03/10-proyectos-open-source-gsoc-2010) para continuar con su desarrollo (también para mejorar el logo, que es horrendo).

Fuente: [Bitelia](https://bitelia.com/2010/04/comando-linux-nast)

Via: [LinuxParty](https://www.linux-party.com/modules.php?name=News&file=article&sid=5719:saber-quien-est%E1-utilizando-tu-red,-wifi-incluida.)

Proyecto: [NAST](https://nast.berlios.de/)

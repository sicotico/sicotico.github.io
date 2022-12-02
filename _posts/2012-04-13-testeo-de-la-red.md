---

title: "Testeo de la red"
date: "2012-04-13"
categories: 
  - "sin-categoria"
---

Tras terminar el nuevo sistema funcionando toca el momento de configurar la red. Teniendo un servidor de archivos  , NFS , toca el momento de comprobar la velocidad de transferencia.

Desde Dolphin podemos utilizar los kioslave , o eso era como se llamaban antes en konqueror. Con estas herramientas podemos conectarnos por varios protocolos usando solo el explorador de archivos , siempre me pareció una mierda pero si hay prisa ahí siempre está. Esta vez con pruebas en la mano descubro que tengo trasferencia de 15MBytes/sec mantenidos , ¡ Vaya mierda !.

Toca configurar correctamente las tarjetas de red y utilizar un test de de rendimiento de red. Para estas tareas utilizaremos "ethtool" e "iperf". Primero revisar que las tarjetas negocia a Gigabit. **Servidor:**

Supported ports: \[ TP \]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Advertised pause frame use: Symmetric
Advertised auto-negotiation: Yes
Speed: 1000Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
MDI-X: Unknown
Supports Wake-on: g
Wake-on: g
Current message level: 0x000000ff (255)
drv probe link timer ifdown ifup rx\_err tx\_err
Link detected: yes

 **Cliente:**

Settings for eth0:
        Supported ports: \[ MII \]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Link detected: yes

Podemos comprobar que las dos están correctamente configuradas , en red de Gigabit.

**Prueba 1:** Dolphin con Kioslave

Un simple copia y pega de un fichero de 4GB me desilusiona con 15MB/s mantenidos. HAce llorar a cualquiera , una Ubuntu Server mínima debería de proporcionar mejores resultados.

**Testeo de la red** Lo primero es utilizar una prueba estandar de medición , para ello utilizaré el iperf. Una aplicación cliente-servido con el que es facilísimo medir tasas de trasferencias.

En uno de los dos equipos ejecutamos el servidor de iperf , bloqueara un terminal. `iperf -s -f K` `iperf -c IP/Hostname -f K`

- \-s modo servidor
- \-c modo cliente , necesita la IP/hostname del servidor
- \-f define las unidades a utilizar K= Kbytes,M=Mbytes,m=Mbits,....
- \-t define el tiempo (en segundos) de la prueba, a mas tiempo se obtendrá un resultado más real

 

iperf -c servidor -f M -t 360
------------------------------------------------------------
Client connecting to servidor, TCP port 5001
TCP window size: 0.02 MByte (default)
------------------------------------------------------------
\[  3\] local servidor port 43107 connected with cliente port 5001
 
\[ ID\] Interval       Transfer     Bandwidth
\[  3\]  0.0-360.0 sec  40349 MBytes   112 MBytes/sec

 

Super contento con el resultado , tenia que encontrar el problema del bajo rendimiento. Siguiente prueba ...

 

**Prueba 2:**

Montar el recurso y copiar usando Dolphin

Con el mismo fichero de la prueba anterior , en la misma localización de origen y la misma de destino , obtenemos 30MBytes/sec mantenidos.

Un simple copia y pega de un fichero de 4GB me desilusiona con 15MB/s mantenidos. Hace llorar a cualquiera , una Ubuntu Server mínima debería de proporcionar

**Conclusión**

Con montar el sistema de fichero duplicamos el rendimiento , demasiadas funcionalidades para Dolphi. ¿Que fue de esa filosofia KISS o una herramienta para una tarea y que la haga bien?

**Fuentes:**

[amperis.blogspot.com.es test de velocidad entre dos puntos(Linux)](https://amperis.blogspot.com.es/2010/06/test-de-velocidad-entre-dos-puntos-de.html) [serverfault.com ¿how to check the physical status of an ethernet port in linux?](https://serverfault.com/questions/15776/how-to-check-the-physical-status-of-an-ethernet-port-in-linux)

---

title: "Oracle en Linux"
date: "2009-10-19"
categories: 
  - "sin-categoria"
---

Hace tiempo explicamos como usar los comando [oradim](https://luispuente.net/2009/05/27/oracle-listener/) para windows , pues hoy toca explicar un poquito su homologa para la plataforma linux.

Estas son `dbstart` y `dbshut`. Se encuentra en `/opt/oracle/product/10.2.0/client/bin/` , como parametros reciben las instacias las cuales arracaran o parara respectivamente. Estos se alamacenan en el fichero `/etc/oratab` con el siguiente formato:

`$ORACLE_SID:ORACLE_HOME::`

Yo no entiendo muy bien esta parte asi que lo que hago es pasar el parametro de la instacia directamente al comando `dbstart` o `sdbshut` , asi:

<`dbstart` | `dbshut` > `$ORACLE_HOME/oradata/` nombre de la instancia

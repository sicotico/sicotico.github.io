---
layout: single
title: "Oracle listener"
date: "2009-05-27"
categories: software
---

Como aprendí

Me lo cargue , el listener lo había borrado pero el servicio de windows asociado ahí seguía , un `sc delete nombre_del_servicio`. Ahora empieza el quebradero de cabeza ya que tras crear uno nuevo LISTENER su servicio asociado me dice que no existe .

Mínima teoría

El listener es un servicio que registra las instancias y dirigir las consultas . Se controla mediante la consola gráfica "Net Configuration"   , o un asistente más cómodo "Net Configuration Assistant" . Para combar el estado utilizo el comando `lsnrctl status` El orden correcto de arranque sería primero el Listener y después la DB

La solución

Baje la base datos y borre todos los LISTENER con la "Net Configuration Assistan" , tuve que borrar varias veces , hasta que el menú me dijera que no podía borrar nada.  Reinicie el servidor , cree un nuevo listener y lo inicie a mano con "lsnrctl start LISTENER" se creo solo el servicio. Ahora levante la base de datos y revise el Listener para comprobar que la hubiera registrado.

Para más precisión esto fue los pasos que seguí:

con un sqlplus

`sqlplus /nolog`

`connect / as sysdba`

`shutdow`

Se puede usar `oradim -shutdown-sid dbblog`

Reiniciamos el servidor

Con el "Net Configuration Assistant" creo un nuevo listener

`lsnrclt status`

`Listening Endpoints Summary... (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=wk3)(PORT=1521))) The listener supports no services The command completed successfully`

`sqlplus /nolog`

`connect / as sysdba`

`startup`

O podemos usar Oradim

`oradim -startup -sid dbblog`

Revisamos el listener y verificamos que haya registrado nuestra BD=dbblog

`lsnrclt status`

`Listening Endpoints Summary... (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=wk3)(PORT=1521))) Services Summary... Service "dbblog" has 1 instance(s). Instance "dbblog", status READY, has 1 handler(s) for this service... Service "dbblog_XPT" has 1 instance(s). Instance "dbblog", status READY, has 1 handler(s) for this service... The command completed successfully`

Ya tenemos la base de datos levanta y registrada , ahora ya podemos conectarnos

`sqlplus [USER]/[PASSWORD]@[SID]`

---
layout: single
title: "Chuletario de consultas Oracle"
date: "2010-03-02"
categories: software
---

Buscaba como calcular el tamaño de las tablas de una base de datos y me encontré con este chuletario de oracle.

La fuente es [Consultas de Oracle .](https://www.davidsuarez.es/2008/01/consultas-de-oracle/)

##### Consulta Oracle SQL para conocer Vista que muestra el estado de la base de datos:

select \* from v$instance

##### Consulta Oracle SQL para conocer Consulta que muestra si la base de datos está abierta

select status from v$instance

##### Consulta Oracle SQL para conocer Vista que muestra los parámetros generales de Oracle

select \* from v$system\_parameter

##### Consulta Oracle SQL para conocer Versión de Oracle

select value from v$system\_parameter where name = ‘compatible’

##### Consulta Oracle SQL para conocer Ubicación y nombre del fichero spfile

select value from v$system\_parameter where name = ’spfile’

##### Consulta Oracle SQL para conocer Ubicación y número de ficheros de control

select value from v$system\_parameter where name = ‘control\_files’

##### Consulta Oracle SQL para conocer Nombre de la base de datos

select value from v$system\_parameter where name = ‘db\_name’

##### Consulta Oracle SQL para conocer Vista que muestra las conexiones actuales a Oracle Para visualizarla es necesario entrar con privilegios de administrador

select osuser, username, machine, program from v$session order by osuser

##### Consulta Oracle SQL para conocer Vista que muestra el número de conexiones actuales a Oracle agrupado por aplicación que realiza la conexión

select program Aplicacion, count(program) Numero\_Sesiones from v$session group by program order by Numero\_Sesiones desc

##### Consulta Oracle SQL para conocer Vista que muestra los usuarios de Oracle conectados y el número de sesiones por usuario

select username Usuario\_Oracle, count(username) Numero\_Sesiones from v$session group by username order by Numero\_Sesiones desc Propietarios de objetos y número de objetos por propietario select owner, count(owner) Numero from dba\_objects group by owner order by Numero desc

##### Consulta Oracle SQL para conocer Diccionario de datos (incluye todas las vistas y tablas de la Base de Datos)

select \* from dictionary

##### Consulta Oracle SQL para conocer Muestra los datos de una tabla especificada (en este caso todas las tablas que lleven la cadena “XXX”

select \* from ALL\_ALL\_TABLES where upper(table\_name) like ‘%XXX%’

##### Consulta Oracle SQL para conocer Tablas propiedad del usuario actual

select \* from user\_tables

##### Consulta Oracle SQL para conocer Todos los objetos propiedad del usuario conectado a Oracle

select \* from user\_catalog

##### Consulta Oracle SQL para conocer Consulta SQL para el DBA de Oracle que muestra los tablespaces, el espacio utilizado, el espacio libre y los ficheros de datos de los mismos:

Select t.tablespace\_name “Tablespace”, t.status “Estado”, ROUND(MAX(d.bytes)/1024/1024,2) “MB Tamaño”, ROUND((MAX(d.bytes)/1024/1024) - (SUM(decode(f.bytes, NULL,0, f.bytes))/1024/1024),2) “MB Usados”, ROUND(SUM(decode(f.bytes, NULL,0, f.bytes))/1024/1024,2) “MB Libres”, t.pct\_increase “% incremento”, SUBSTR(d.file\_name,1,80) “Fichero de datos” FROM DBA\_FREE\_SPACE f, DBA\_DATA\_FILES d, DBA\_TABLESPACES t WHERE t.tablespace\_name = d.tablespace\_name AND f.tablespace\_name(+) = d.tablespace\_name AND f.file\_id(+) = d.file\_id GROUP BY t.tablespace\_name, d.file\_name, t.pct\_increase, t.status ORDER BY 1,3 DESC

##### Consulta Oracle SQL para conocer Productos Oracle instalados y la versión:

select \* from product\_component\_version

##### Consulta Oracle SQL para conocer Roles y privilegios por roles:

select \* from role\_sys\_privs

<script type="text/javascript">// <![CDATA[ google_ad_client = "pub-1398624141972736"; /* 300x250, creado 10/07/08 */ google_ad_slot = "4038058567"; google_ad_width = 300; google_ad_height = 250; // ]]></script>

 

<script src="https://pagead2.googlesyndication.com/pagead/show_ads.js" type="text/javascript"></script>

<script type="text/javascript">// <![CDATA[ google_protectAndRun("ads_core.google_render_ad", google_handleError, google_render_ad); // ]]></script>

##### Consulta Oracle SQL para conocer Reglas de integridad y columna a la que afectan:

select constraint\_name, column\_name from sys.all\_cons\_columns

##### Consulta Oracle SQL para conocer Tablas de las que es propietario un usuario, en este caso “xxx”:

SELECT table\_owner, table\_name from sys.all\_synonyms where table\_owner like ‘xxx’

##### Consulta Oracle SQL para conocer Otra forma más efectiva (tablas de las que es propietario un usuario):

SELECT DISTINCT TABLE\_NAME FROM ALL\_ALL\_TABLES WHERE OWNER LIKE ‘HR’ Parámetros de Oracle, valor actual y su descripción: SELECT v.name, v.value value, decode(ISSYS\_MODIFIABLE, ‘DEFERRED’, ‘TRUE’, ‘FALSE’) ISSYS\_MODIFIABLE, decode(v.isDefault, ‘TRUE’, ‘YES’, ‘FALSE’, ‘NO’) “DEFAULT”, DECODE(ISSES\_MODIFIABLE, ‘IMMEDIATE’, ‘YES’,'FALSE’, ‘NO’, ‘DEFERRED’, ‘NO’, ‘YES’) SES\_MODIFIABLE, DECODE(ISSYS\_MODIFIABLE, ‘IMMEDIATE’, ‘YES’, ‘FALSE’, ‘NO’, ‘DEFERRED’, ‘YES’,'YES’) SYS\_MODIFIABLE , v.description FROM V$PARAMETER v WHERE name not like ‘nls%’ ORDER BY 1

##### Consulta Oracle SQL para conocer Usuarios de Oracle y todos sus datos (fecha de creación, estado, id, nombre, tablespace temporal,…):

Select \* FROM dba\_users

##### Consulta Oracle SQL para conocer Tablespaces y propietarios de los mismos:

select owner, decode(partition\_name, null, segment\_name, segment\_name || ‘:’ || partition\_name) name, segment\_type, tablespace\_name,bytes,initial\_extent, next\_extent, PCT\_INCREASE, extents, max\_extents from dba\_segments Where 1=1 And extents > 1 order by 9 desc, 3

##### Últimas consultas SQL ejecutadas en Oracle y usuario que las ejecutó:

select distinct vs.sql\_text, vs.sharable\_mem, vs.persistent\_mem, vs.runtime\_mem, vs.sorts, vs.executions, vs.parse\_calls, vs.module, vs.buffer\_gets, vs.disk\_reads, vs.version\_count, vs.users\_opening, vs.loads, to\_char(to\_date(vs.first\_load\_time, ‘YYYY-MM-DD/HH24:MI:SS’),’MM/DD HH24:MI:SS’) first\_load\_time, rawtohex(vs.address) address, vs.hash\_value hash\_value , rows\_processed , vs.command\_type, vs.parsing\_user\_id , OPTIMIZER\_MODE , au.USERNAME parseuser from v$sqlarea vs , all\_users au where (parsing\_user\_id != 0) AND (au.user\_id(+)=vs.parsing\_user\_id) and (executions >= 1) order by buffer\_gets/executions desc

##### Consulta Oracle SQL para conocer todos los Tablespaces:

select \* from V$TABLESPACE

##### Consulta Oracle SQL para conocer Memoria Share\_Pool libre y usada

select name,to\_number(value) bytes from v$parameter where name =’shared\_pool\_size’ union all select name,bytes from v$sgastat where pool = ’shared pool’ and name = ‘free memory’ Cursores abiertos por usuario select b.sid, a.username, b.value Cursores\_Abiertos from v$session a, v$sesstat b, v$statname c where c.name in (‘opened cursors current’) and b.statistic# = c.statistic# and a.sid = b.sid and a.username is not null and b.value >0 order by 3

##### Consulta Oracle SQL para conocer Aciertos de la caché (no debería superar el 1 por ciento)

select sum(pins) Ejecuciones, sum(reloads) Fallos\_cache, trunc(sum(reloads)/sum(pins)\*100,2) Porcentaje\_aciertos from v$librarycache where namespace in (‘TABLE/PROCEDURE’,'SQL AREA’,'BODY’,'TRIGGER’); Sentencias SQL completas ejecutadas con un texto determinado en el SQL SELECT c.sid, d.piece, c.serial#, c.username, d.sql\_text FROM v$session c, v$sqltext d WHERE c.sql\_hash\_value = d.hash\_value and upper(d.sql\_text) like ‘%WHERE CAMPO LIKE%’ ORDER BY c.sid, d.piece Una sentencia SQL concreta (filtrado por sid) SELECT c.sid, d.piece, c.serial#, c.username, d.sql\_text FROM v$session c, v$sqltext d WHERE c.sql\_hash\_value = d.hash\_value and sid = 105 ORDER BY c.sid, d.piece

##### Consulta Oracle SQL para conocer Tamaño ocupado por la base de datos

select sum(BYTES)/1024/1024 MB from DBA\_EXTENTS

##### Consulta Oracle SQL para conocer Tamaño de los ficheros de datos de la base de datos

select sum(bytes)/1024/1024 MB from dba\_data\_files

##### Consulta Oracle SQL para conocer Tamaño ocupado por una tabla concreta sin incluir los índices de la misma

select sum(bytes)/1024/1024 MB from user\_segments where segment\_type=’TABLE’ and segment\_name=’NOMBRETABLA’

##### Consulta Oracle SQL para conocer Tamaño ocupado por una tabla concreta incluyendo los índices de la misma

select sum(bytes)/1024/1024 Table\_Allocation\_MB from user\_segments where segment\_type in (‘TABLE’,'INDEX’) and (segment\_name=’NOMBRETABLA’ or segment\_name in (select index\_name from user\_indexes where table\_name=’NOMBRETABLA’))

##### Consulta Oracle SQL para conocer Tamaño ocupado por una columna de una tabla

select sum(vsize(‘NOMBRECOLUMNA’))/1024/1024 MB from NOMBRETABLA

##### Consulta Oracle SQL para conocer Espacio ocupado por usuario

SELECT owner, SUM(BYTES)/1024/1024 FROM DBA\_EXTENTS MB group by owner

##### Consulta Oracle SQL para conocer Espacio ocupado por los diferentes segmentos (tablas, índices, undo, rollback, cluster, …)

SELECT SEGMENT\_TYPE, SUM(BYTES)/1024/1024 FROM DBA\_EXTENTS MB group by SEGMENT\_TYPE

##### Consulta Oracle SQL para conocer Obtener todas las funciones de Oracle: NVL, ABS, LTRIM, … SELECT distinct object\_name

FROM all\_arguments WHERE package\_name = ‘STANDARD’ order by object\_name

##### Consulta Oracle SQL para conocer Espacio ocupado por todos los objetos de la base de datos, muestra los objetos que más ocupan primero

SELECT SEGMENT\_NAME, SUM(BYTES)/1024/1024 FROM DBA\_EXTENTS MB group by SEGMENT\_NAME order by 2 desc

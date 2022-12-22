---
layout: posts
title: "Listar tablas en Oracle"
date: "2010-01-26"
categories: software
---

La gestión de las tablas en **Oracle** resulta diferente a como lo hace **MySQL**, pero resulta mucho más flexible una vez acostumbrados a ella. Vamos a ver como realizar **listados de tablas** por **tablespace** o por **usuario**.

Para poder realizar listados de tablas podemos consultar varias tablas del **data dictionary**:

- **DBA\_TABLES**: Contiene todas las tablas de la base de datos
- **ALL\_TABLES**: Contiene todas las tablas accesibles por el usuario (las propias más las que tiene permisos sobre ellas)
- **USER\_TABLES**: Contiene totas las tablas del usuario
- **DBA\_SEGMENTS**: Contiene todos los segmentos de la base de datos, esto incluye tablas, indices y segmentos de rollback entre otros:

SQL> select distinct SEGMENT\_TYPE from DBA\_SEGMENTS;

SEGMENT\_TYPE
------------------
LOBINDEX
INDEX PARTITION
TABLE PARTITION
NESTED TABLE
ROLLBACK
LOB PARTITION
LOBSEGMENT
INDEX
TABLE
CLUSTER
TYPE2 UNDO

11 filas seleccionadas.

Así, la tabla **DBA\_SEGMENTS** contiene la tabla **DBA\_TABLES** más el resto de segmentos de la base de datos:

SQL> select count(\*) from DBA\_SEGMENTS;

  COUNT(\*)
----------
      5783

SQL> select count(\*) from DBA\_TABLES;

  COUNT(\*)
----------
      2083

Usando la tabla **DBA\_TABLES** tenemos las siguientes columnas:

SQL> desc DBA\_TABLES;
 Nombre                                    ?Nulo?   Tipo
 ----------------------------------------- -------- ----------------------------
 OWNER                                     NOT NULL VARCHAR2(30)
 TABLE\_NAME                                NOT NULL VARCHAR2(30)
 TABLESPACE\_NAME                                    VARCHAR2(30)
 CLUSTER\_NAME                                       VARCHAR2(30)
 IOT\_NAME                                           VARCHAR2(30)
 STATUS                                             VARCHAR2(8)
 PCT\_FREE                                           NUMBER
 PCT\_USED                                           NUMBER
 INI\_TRANS                                          NUMBER
 MAX\_TRANS                                          NUMBER
 INITIAL\_EXTENT                                     NUMBER
 NEXT\_EXTENT                                        NUMBER
 MIN\_EXTENTS                                        NUMBER
 MAX\_EXTENTS                                        NUMBER
 PCT\_INCREASE                                       NUMBER
 FREELISTS                                          NUMBER
 FREELIST\_GROUPS                                    NUMBER
 LOGGING                                            VARCHAR2(3)
 BACKED\_UP                                          VARCHAR2(1)
 NUM\_ROWS                                           NUMBER
 BLOCKS                                             NUMBER
 EMPTY\_BLOCKS                                       NUMBER
 AVG\_SPACE                                          NUMBER
 CHAIN\_CNT                                          NUMBER
 AVG\_ROW\_LEN                                        NUMBER
 AVG\_SPACE\_FREELIST\_BLOCKS                          NUMBER
 NUM\_FREELIST\_BLOCKS                                NUMBER
 DEGREE                                             VARCHAR2(10)
 INSTANCES                                          VARCHAR2(10)
 CACHE                                              VARCHAR2(5)
 TABLE\_LOCK                                         VARCHAR2(8)
 SAMPLE\_SIZE                                        NUMBER
 LAST\_ANALYZED                                      DATE
 PARTITIONED                                        VARCHAR2(3)
 IOT\_TYPE                                           VARCHAR2(12)
 TEMPORARY                                          VARCHAR2(1)
 SECONDARY                                          VARCHAR2(1)
 NESTED                                             VARCHAR2(3)
 BUFFER\_POOL                                        VARCHAR2(7)
 ROW\_MOVEMENT                                       VARCHAR2(8)
 GLOBAL\_STATS                                       VARCHAR2(3)
 USER\_STATS                                         VARCHAR2(3)
 DURATION                                           VARCHAR2(15)
 SKIP\_CORRUPT                                       VARCHAR2(8)
 MONITORING                                         VARCHAR2(3)
 CLUSTER\_OWNER                                      VARCHAR2(30)
 DEPENDENCIES                                       VARCHAR2(8)
 COMPRESSION                                        VARCHAR2(8)
 DROPPED                                            VARCHAR2(3)

Los campos que vamos a ver son los siguientes:

- **OWNER**: Propietario del segmento
- **SEGMENT\_NAME**: Nombre del segmento
- **TABLESPACE\_NAME**: Nombre del tablespace al que pertenece

Mediante simples **consultas SQL** podemos obtener los datos que queremos. Por ejemplo, para **listar el nombre de todas las tablas** de la base de datos **Oracle** haríamos:

SQL> select TABLE\_NAME from DBA\_TABLES;
TABLE\_NAME
------------------------------
OPINIONES
FORM
LOCALIDAD
EXAMENES
(...)

2083 filas seleccionadas.

Este comando sería el equivalente al **SHOW TABLES;** de **MySQL**.

Para **contar todas las tablas del tablespace** UNIT001 haríamos lo siguiente:

SQL> select count(\*) from DBA\_TABLES where TABLESPACE\_NAME='UNIT001';

  COUNT(\*)
----------
       117

Y para **contar las tablas de cada usuario** podríamos hacer lo siguiente:

SQL> select count(\*), OWNER from DBA\_TABLES group by OWNER;

  COUNT(\*) OWNER
---------- ------------------------------
        49 MDSYS
        24 EJEMPLOSCURSO
        14 NURIA
         1 TSMSYS
         2 DMSYS
       160 OING
         3 OUTLN
        37 CTXSYS
       126 OLAPSYS
        35 ENRIC\_COLL
         6 NEWS

  COUNT(\*) OWNER
---------- ------------------------------
       141 SYSTEM
        68 TESTING
        44 EXFSYS
         4 TIGER
        37 TIENDA
        11 SYSTEMADMIN\_ES
        21 DBSNMP
         4 ORDSYS
       337 SYSMAN
        11 XDB
        66 CLAUDATOR

  COUNT(\*) OWNER
---------- ------------------------------
        75 XD\_TMP
       767 SYS
        40 WMSYS

25 filas seleccionadas.

Fuente: [Listar tablas en Oracle](https://www.linux-party.com/modules.php?name=News&file=article&sid=5444:listar-las-tablas-en-oracle)

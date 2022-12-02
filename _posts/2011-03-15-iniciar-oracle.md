---

title: "Iniciar Oracle"
date: "2011-03-15"
categories: 
  - "sin-categoria"
---

\-> lsnrctl

\-> status

C:Documents and SettingsAdministrator>lsnrctl

LSNRCTL for 32-bit Windows: Version 10.2.0.1.0 - Production on 16-MAR-2009 11:01 :24

Copyright (c) 1991, 2005, Oracle. All rights reserved.

Welcome to LSNRCTL, type "help" for information.

LSNRCTL> status Connecting to (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1521)) STATUS of the LISTENER ------------------------ Alias LISTENER Version TNSLSNR for 32-bit Windows: Version 10.2.0.1.0 - Produ ction Start Date 16-MAR-2009 10:39:19 Uptime 0 days 0 hr. 22 min. 16 sec Trace Level off Security ON: Local OS Authentication SNMP OFF Listener Log File C:oracleproduct10.2.0db\_2networkloglistener.log

Listening Endpoints Summary... (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=wk3)(PORT=1521))) The listener supports no services The command completed successfully

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* \*( Aqui vemos que la base de datos no se ha iniciado )\* \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

\-> cmd

\-> sqlplus /nolog

\-> connect / as sysdba; Connect to an idle instance

\-> startup

SQL> startup ORACLE instance started.

Total System Global Area 167772160 bytes Fixed Size 1247900 bytes Variable Size 79693156 bytes Database Buffers 83886080 bytes Redo Buffers 2945024 bytes Database mounted. Database opened.

SQL> exit

C:Documents and SettingsAdministrator>lsnrctl

LSNRCTL for 32-bit Windows: Version 10.2.0.1.0 - Production on 16-MAR-2009 11:01 :24

Copyright (c) 1991, 2005, Oracle. All rights reserved.

Welcome to LSNRCTL, type "help" for information.

LSNRCTL> status Connecting to (ADDRESS=(PROTOCOL=tcp)(HOST=)(PORT=1521)) STATUS of the LISTENER

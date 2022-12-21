---
layout: post
title: "Oracle-XE en Debian-6-64bits"
date: "2011-08-25"
categories: software
---

Que cosas me escribe en la lista de correo , desde luego son bonitas.

root@viper-v0:~# sudo dpkg -i --force-architecture oracle-xe.deb dpkg: warning: overriding problem because --force enabled: package architecture (i386) does not match system (amd64) (Reading database ... 37471 files and directories currently installed.) Unpacking oracle-xe-universal (from oracle-xe.deb) ... Setting up oracle-xe-universal (10.2.0.1-1.1) ... insserv: warning: script 'oracle-xe' missing LSB tags and overrides Executing Post-install steps...

-e You must run '/etc/init.d/oracle-xe configure' as the root user to configure the database.

root@viper-v0:~# /etc/init.d/oracle-xe configure

Oracle Database 10g Express Edition Configuration -------------------------------------------------

This will configure on-boot properties of Oracle Database 10g Express Edition. The following questions will determine whether the database should be starting upon system boot, the ports it will use, and the passwords that will be used for database accounts. Press to accept the defaults. Ctrl-C will abort.

Specify the HTTP port that will be used for Oracle Application Express \[8080\]:

Specify a port that will be used for the database listener \[1521\]:

Specify a password to be used for database accounts. Note that the same password will be used for SYS and SYSTEM. Oracle recommends the use of different passwords for each database account.

This can be done after initial configuration:

Confirm the password:

Do you want Oracle Database 10g Express Edition to be started on boot (y/n) \[y\]:

Starting Oracle Net Listener...

Done Configuring Database...

Done Starting Oracle Database 10g Express Edition Instance...

Done Installation Completed Successfully.

To access the Database Home Page go to "https://127.0.0.1:8080/apex"

root@viper-v0:/srv# ./lib/oracle/xe/app/oracle/product/10.2.0/server/config/scripts/sqlplus.sh /srv/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls\_lang.sh: 114: \[\[: not found /srv/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls\_lang.sh: 114: \[\[: not found

SQL\*Plus: Release 10.2.0.1.0 - Production on Wed Aug 10 04:35:44 2011

Copyright (c) 1982, 2005, Oracle. All rights reserved.

SQL>

---
layout: post
title: "Cambiar el SGA a Oracle"
date: "2011-02-25"
categories: software
---

SQL> show sga

Total System Global Area 1073741824 bytes Fixed Size                  2071184 bytes Variable Size             432014704 bytes Database Buffers          633339904 bytes Redo Buffers                6316032 bytes SQL> show parameters cache

NAME                                 TYPE        VALUE ------------------------------------ ----------- ------------------------------ db\_cache\_advice                      string      ON db\_cache\_size                        big integer 0 db\_keep\_cache\_size                   big integer 0 db\_recycle\_cache\_size                big integer 0 db\_16k\_cache\_size                    big integer 0 db\_2k\_cache\_size                     big integer 0 db\_32k\_cache\_size                    big integer 0 db\_4k\_cache\_size                     big integer 0 db\_8k\_cache\_size                     big integer 0 object\_cache\_max\_size\_percent        integer     10 object\_cache\_optimal\_size            integer     102400

NAME                                 TYPE        VALUE ------------------------------------ ----------- ------------------------------ session\_cached\_cursors               integer     20 SQL> show parameter sga

NAME                                 TYPE        VALUE ------------------------------------ ----------- ------------------------------ lock\_sga                             boolean     FALSE pre\_page\_sga                         boolean     FALSE sga\_max\_size                         big integer 1G    -------> Lo maximo que se puede usar , reserva memoria sga\_target                           big integer 1G         -------> marca la memoria a utilizar simepre por debajo o igual que sg\_max\_size SQL> alter system set SGA\_MAX\_SIZE=2G scope=both; alter system set SGA\_MAX\_SIZE=2G scope=both \* ERROR en lÝnea 1: ORA-02095: el parßmetro de inicializaci¾n especificado no se puede modificar

SQL> alter system set SGA\_MAX\_SIZE=2G scope=spfile;

Sistema modificado.

SQL> alter system set SGA\_TARGET=2G scope=spfile;

Sistema modificado.

SQL> shutdown immediate;

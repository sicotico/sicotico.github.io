---

title: "Función TO_DATE"
date: "2011-09-20"
categories: 
  - "sin-categoria"
---

En Oracle / PLSQL, la función TO\_DATE convierte una cadena a una fecha , siempre que esta tenga un formato correcto.

La sintaxis de la función TO\_DATE es la siguiente:

to\_date (cadena1, \[format\_mask\], \[nls\_language\])

- **cadena1** es la cadena que se convierte en una fecha.
- **format\_mask** es opcional. Este es el formato que se utilizará para convertir cadena1 a una fecha.
- **nls\_language** es opcional. Este es el lenguaje nls para convertir cadena1 a una fecha.

La siguiente es una lista de opciones para el parámetro format\_mask. Estos parámetros se pueden utilizar en muchas combinaciones.

Explicación de los parámetros

-     YEAR Año AÑO, expuso
-     YYYY cuatro dígitos del año
-     YYY,YY,Y los últimos 3, 2 ó 1 dígito (s) del año.
-     IYY,IY,I Últimos 3 I, 2, o 1 dígito (s) del año ISO.
-     IYYY año de 4 dígitos basado en el estándar ISO
-     RRRR Acepta un año de 2 dígitos y devuelve un año de 4 dígitos.
- -     Un valor entre 0-49 volverá un año 20xx.
    -     Un valor entre 50-99 volverá un año 19xx.
-     Q trimestre del año (1, 2, 3, 4, enero-marzo = 1).
-     MM Mes (01-12; ENE = 01).
-     MON Nombre abreviado del mes.
-     MONTH Nombre del mes de mes, rellena con espacios en blanco a la longitud de 9 caracteres.
-     RM mes número romano (I-XII, JAN = I).
-     WW Semana del año (1-53) donde la semana 1 comienza el primer día del año y continúa hasta el séptimo día del año.
-     W semana del mes (1-5) en una semana comienza el primer día del mes y termina en el séptimo.
-     IW semana del año (1-52 o 1-53) basado en el estándar ISO.
-     D Día de la semana (1-7).
-     Santo del día del día.
-     DD Día del mes (1-31).
-     Día de DDD del año (1-366).
-     DY Nombre abreviado del día.
-     J Julian día, el número de días desde el 1 de enero de 4712 antes de Cristo.
-     HH Hora del día (1-12).
-     HH12 Hora del día (1-12).
-     HH24 Hora del día (0-23).
-     MI Minutos (0-59).
-     SS segundo (0-59).
-     Segundos después de la medianoche SSSSS (0-86.399).
-     FF fraccional segundos. Utilice un valor entre 1 y 9 después de FF para indicar el número de dígitos de las fracciones de segundo. Por ejemplo, 'FF4.
-     AM, AM, PM, o P.M. Meridiano indicador
-     A.D or AD el indicador
-     BC or B.C. indicador BC

Se puede utilizar en estas versiones Oracle 8i, Oracle 9i, Oracle 10g, Oracle 11g

Ejemplos:

TO\_DATE ('2011/06/07 ',' dd / mm / dd ') devolverá un valor de fecha 7 de junio de 2011. TO\_DATE ('030205 ',' MMDDYY ') devolverá un valor de fecha 3 de marzo de 2005. to\_date ('21120415 ',' YYYYMMDD ') devolverá un valor de fecha de 15 de abril 2112.

to\_date (campo1,' YYYYMMDD ') devolverá el contenido del campo1 con la mascara aplicada

---

title: "Fechas y Oracle"
date: "2011-09-02"
categories: 
  - "sin-categoria"
---

Los elemento que vamos a utilizar son dos tablas y dos campos

- Tabla1 con alias T1
- Tabla2 con alias T2
- campo1 de tipo CHAR
- campo2 de tipo DATE

Convertir de CHAR a DATE

TO\_DATE(T1.campo1, 'YYYY-MM-DD HH24:MI:SS')

Diferencia de días entre dos fechas , obteniendo en días:

TRUNC (TO\_DATE(T1.campo1, 'YYYY-MM-DD HH24:MI:SS') - T2.campo2 )

Puedes usar la fecha de sistema con "SYSDATE" :

TRUNC (TO\_DATE(T1.campo1, 'YYYY-MM-DD HH24:MI:SS') - SYSDATE )

---

title: "Oracle 10g instalación"
date: "2009-05-27"
categories: 
  - "sin-categoria"
---

**Instalación Oracle ,mínimos recursos**

- Desde el cd "database" se instala el motor de base de datos.
    - Hacemos una instalación Personal Edition sin crear ninguna base de datos
    - En la instalación Personal Edition no tenemos acceso al HOME del motor de bases de datos , así que cuando instalemos el cliente solo conoceremos la ruta "path" de instalación

- Desde el cd "cliente" instalamos el cliente y las herramientas de administración.
    - La opción a elegir es Administrador , contiene herramientas y el cliente
    - Crear DB
    - Uso General
    - Nombre global , es el mismo que el SID
    - Deshabilitamos el Enterprise Manager , es un gestor web para esta base de datos y consume muchos recursosç
    - La contraseña que pongo para todas las cuentas la misma "a"
    - Marcamos la opción Sistema de Archivos. Porque son entorno Virtuales o de PCs personales
    - Seleccionamos la ruta de la DB , lo normal es crearla dentro de la carpeta oracleoradata
        - Ej c:oracleproduct10.2.1db\_1 --> Motor de DB c:oracleoradata|"nombre de DB" --> Mi DB
    - Desmarcar la opción "Especificar Área de Recuperación de Flash" , ocupa muchísimo y no lo se usar
    - Desmarcar la opción "Esquema de Ejemplo" , mi aplicación ya los creara o me dirá como , solo creamos la instancia en blanco
    - Nos informa de la memoria que queremos asignar , con la recomendanción de hacerla lo mas pequeño posible para entorno de pruebas revisar la sección de requisitos de la aplicación
    - El resto de pestañas viene por defecto y nos son validas
    - Revisamos varias paginar de resumen
    - Marcamos la opción "Crear Base de Datos"
    - Deshabilitamos las demás , no queremos scripts ni que sea plantilla
    - Revisar que exista un servicio de nombre Listener , si no existe podemos utilizamos :
    - En el Menu "Configuration and Migration Tools"
    - Net Configuration Assistant --> Asistonto Net Manager --> Más profesional
    - Gestion de DB Oracle
    - El Administrador de oracle es "Enterprise Manager Console"
    - El listener de oracle no registra las bases de datos y las tenemos que añadir a mano , la primera vez aparece un asistente.

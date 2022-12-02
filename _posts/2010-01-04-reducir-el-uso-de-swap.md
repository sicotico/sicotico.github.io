---

title: "Reducir el uso de swap"
date: "2010-01-04"
categories: 
  - "sin-categoria"
---

\- Verificar el valor inicial de la swappiness. En el terminal escribimos:

`$ sudo cat /proc/sys/vm/swappiness`

introducimos la contraseña y tecleamos enter, y nos mostrará un valor de 60 (si nos llegara a mostrar 10, ya no hay que hacer nada aquí).

\- Luego probamos el sistema a ver como funciona si reducimos el valor a 10. En el terminal:

`$ sudo sysctl -w vm.swappiness=10`

(Este cambio es temporal , solo hasta que se reinicie)

Debemos de dar caña al ordenador para comprobar que el valor es valido para nuestro caso

Hacer el cambio permanente. En el terminal:

`$ sudo vi /etc/sysctl.conf`

y en la última linea añadimos:

`vw.swappines=10`

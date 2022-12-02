---

title: "CentOS en 5 minutos"
date: "2011-02-22"
categories: 
  - "sin-categoria"
---

**Versión instalada :**

`[root@ns ~]$ cat /etc/*release*`

`cat: /etc/lsb-release.d: Is a directory`

`CentOS release 5.2 (Final)`

**Españolizar:**

Actualizar listado de repositorios

`# yum update`

Tipo de teclado

`# echo KEYBOARDTYPE=”pc” > /etc/sysconfig/keyboard`

Idioma del teclado

`# echo KEYTABLE=”es” >> /etc/sysconfig/keyboard`

También puedes editar el fichero directamente

Instalamos los keymap (solo si se nos ha olvido hacerlo en la instalación o damos con un server consolidado americano) `# yum install kbd` `# mkdir -p /lib/kbd/keymaps/i386/qwerty` `# cp /lib/kbd/keymaps/i386/qwerty/es* /lib/kbd/keymaps/i386/qwerty`

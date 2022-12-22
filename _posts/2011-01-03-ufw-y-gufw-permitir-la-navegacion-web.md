---
layout: posts
title: "UFW y GUFW permitir la navegación web"
date: "2011-01-03"
categories: linux
---

He revisado un poco la configuración de este firewall y para cuatro reglas esta bien. Yo empecé con la política _nada entra y nada sale_ es la forma de crear reglas desde la necesidad y solo para ellas. Es mucho más trabajoso.

Tras bloquear el trafico entrante y saliente lo primero que queremos recuperar es la navegación web. En teoría abriendo el puerto 80 en entrada y salida debiera de ser suficiente , al probarlo comprobamos que no es así, nos hace falta también consultar el DNS y las paginas mediante HTTPS.

**Reglas necesarias:**

- Permitir trafico puerto 80 entrada y salida
- Permitir consultas a los servidores DNS por el puerto 53 ( 2 reglas, una por servidor)
- Permitir trafico en el puerto 443 salida en TCP/UDP

**Trafico puerto 80**

Utilizamos la creación de reglas y accedemos a la pestaña simple. Seleccionamos lo siguientes valores:﻿﻿﻿

- Permitir
- Saliente
- TCP
- 80

**Trafico DNS**

![](images/Gufw?action=AttachFile&do=get&target=add_rule_advance.png "Regla avanzada")

Seleccionamos lo siguientes valores:

- Permitir
- Saliente
- Desde: vacío
- A: Ip del DNS  y completamos el puerto 53

**Trafico puerto 443 (HTTPS)**

Utilizamos la creación de reglas y accedemos a la pestaña simple. Seleccionamos lo siguientes valores:﻿﻿﻿

- Permitir
- Saliente
- TCP
- 80

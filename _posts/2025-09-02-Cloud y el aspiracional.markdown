---
layout: post
title:  "Cloud y el aspiracional"
date:   2025-09-02 10:57:08 +0200
tags: [arquitectura]
---

# **Principios Básicos de Arquitectura en la Nube**

La planificación de una autopista se basa en el número de vehículos que se prevé que circularán. Se añaden márgenes para el posible crecimiento futuro, evitando así construir una infraestructura que quede obsoleta desde el principio. Sin embargo, este enfoque tiene riesgos evidentes: cambios económicos, sociales o de comportamiento pueden dejar infrautilizadas estas vías. El resultado: rescates financieros, infraestructuras abandonadas y una enorme inversión que no genera beneficios.

En tecnología, especialmente en el pasado on-premises, se repetía este mismo error.

---

## **Infraestructura On-Premises: La Autopista Sobredimensionada**

En el mundo on-premises, se seguía el mismo enfoque: construir para una demanda futura que rara vez llegaba. Los costos reales quedaban camuflados, repartidos en una gran bolsa de infraestructura que incluía energía, espacio físico y recursos que no siempre se utilizaban de manera eficiente.

Era como construir una autopista con múltiples carriles para un flujo de tráfico que nunca se materializaba. Aunque el objetivo era estar preparados para picos de uso, en la práctica esto resultaba en recursos sobredimensionados y, lo que es peor, en costos ocultos que inflaban el presupuesto.

---

## **El Salto al Cloud: ¿Nueva Autopista o Viejas Costumbres?**

Cuando migramos al cloud, muchas empresas repiten el error de trasladar infraestructuras sobredimensionadas. Este fenómeno se conoce como **"Lift and Shift"**, y aunque es una forma rápida de iniciar una transición, suele replicar los problemas del pasado: costos altos y falta de optimización.

El "Lift and Shift" consiste en mover cargas de trabajo a la nube sin rediseñar su arquitectura, lo que equivale a construir una autopista nueva pero con el mismo diseño ineficiente que la anterior. Aunque el cloud permite pagar solo por lo que usamos, esta ventaja se pierde si no adaptamos nuestras aplicaciones y recursos al modelo basado en la demanda.

---

## **Arquitecturas Aspiracionales: Construyendo para un Futuro que No Ha Llegado**

Las **arquitecturas aspiracionales** son un claro ejemplo de cómo planificar para un futuro incierto puede llevar a gastos innecesarios. Estas arquitecturas se diseñan para soportar un crecimiento que aún no se ha materializado, generando costos desde el primer día sin ofrecer beneficios inmediatos. Este enfoque complica la medición del retorno de inversión (ROI) y puede comprometer los presupuestos de forma significativa.

Un problema añadido es que la velocidad de evolución tecnológica hace que sea prácticamente imposible anticipar los cambios y necesidades futuras. Por ejemplo, frameworks como **Semantic Kernel** y **LangChain**, inicialmente diseñados para ejecutarse en entornos de cómputo estándar, ahora se integran directamente en plataformas avanzadas como **Databricks**, optimizando su desempeño y extendiendo su funcionalidad. Este cambio refleja cómo los paradigmas tecnológicos pueden evolucionar rápidamente, transformando completamente las necesidades y posibilidades de las arquitecturas.

Intentar construir una infraestructura masiva y preparada para todos los posibles cambios futuros sería como planificar una autopista con diez carriles en un lugar donde solo circulan bicicletas. La realidad es que, cuando llegue el momento de necesitar esos diez carriles, las tecnologías y requisitos habrán cambiado tanto que probablemente ni siquiera sean útiles.

En lugar de apostar por estas arquitecturas sobredimensionadas, es mucho más eficiente adoptar un enfoque progresivo: construir lo necesario para cubrir la demanda actual y escalar conforme se presenten las necesidades. Aquí es donde entra en juego la flexibilidad de la nube, permitiendo ajustar los recursos a la demanda en tiempo real.

---

## **La Landing Zone: El Punto de Partida**

Aquí es donde entra en juego la **Landing Zone**: una base inicial de infraestructura en la nube que proporciona lo esencial en términos de seguridad, redes y acceso. Es como empezar con una carretera básica que puede ampliarse según sea necesario, evitando inversiones masivas desde el inicio.

Ejemplo del Cloud Adoption Framework de Azure. Cubre todo tipo de Workloads que se quieran llevar a al cloud

![Integracion OBO-CBO](https://learn.microsoft.com/es-es/azure/cloud-adoption-framework/ready/enterprise-scale/media/azure-landing-zone-architecture-diagram-hub-spoke.svg)

Con este diagrama uno puede llegar a la conclusion erronea de una carga de trabajo a dicional o extra y la verdad es que apenas lleva unas horas más. Por supuesto con truco

---

## **Optimización y Buenas Prácticas en el Cloud**

Para evitar repetir los errores del pasado y maximizar los beneficios de la nube, es esencial:

1. **Analizar las cargas de trabajo**: Cada aplicación tiene requisitos únicos. Algunas pueden mantenerse en VMs, mientras que otras se benefician de arquitecturas serverless o microservicios. Identificar la mejor solución para cada workload es clave.

2. **Aprovechar herramientas nativas del cloud**: Servicios como PaaS o funciones serverless están diseñados para ser más económicos y escalables. Adoptarlos permite evitar los costos fijos de infraestructuras tradicionales.

3. **Adoptar DevOps e Infraestructura como Código (IaC)**: Herramientas como Terraform o AWS CloudFormation permiten automatizar la creación y gestión de recursos, facilitando la optimización continua y reduciendo errores humanos.

4. **Implementar un modelo de consumo responsable**: En lugar de sobreaprovisionar, la nube permite ajustar los recursos en tiempo real según la demanda, asegurando un equilibrio entre costo y rendimiento.

---

## **Conclusión: Construye lo Justo, Crece Cuando Sea Necesario**

La nube ofrece un modelo revolucionario: pagar solo por lo que se usa y escalar según la demanda. Sin embargo, para aprovecharlo plenamente, es fundamental evitar repetir los errores del pasado. En lugar de construir autopistas sobredimensionadas desde el primer día, enfoquémonos en planificar arquitecturas ajustadas y escalables que respondan a las necesidades reales de nuestros proyectos.

Migrar al cloud no se trata solo de trasladar infraestructuras, sino de rediseñar aplicaciones y procesos para aprovechar al máximo las oportunidades que la nube ofrece. Con un enfoque basado en la demanda real y prácticas modernas, podemos garantizar que nuestras inversiones generen beneficios sostenibles y optimicen los recursos desde el primer día.

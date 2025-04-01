---
layout: post
title:  "LM Studio: Probando RAG y API Server en Local"
date:   2025-04-01 11:00:00 +0200
tags: [IA]
---

# LM Studio: Probando RAG y API Server en Local

## Introducción

El mundo de los modelos de lenguaje ha evolucionado rápidamente, y en la actualidad, la posibilidad de ejecutarlos en local ha ganado relevancia para arquitectos de cloud y desarrolladores que buscan autonomía y control sobre sus datos. En mi caso, como arquitecto con experiencia en infraestructura y plataforma, me interesaba explorar cómo los LLMs en local pueden integrarse con sistemas distribuidos y proporcionar soluciones eficientes sin depender de servicios en la nube.

Recientemente, pasé un día configurando **LM Studio** como un servidor API, probando su capacidad de **Retrieval-Augmented Generation (RAG)** y verificando su integración con una aplicación web en mi red doméstica. Aquí te comparto los detalles de esta experiencia y los aprendizajes clave.

---

## Configuración Inicial de LM Studio y Private LLMs

Para comenzar, actualicé **LM Studio**, una aplicación que facilita la gestión y uso de modelos de lenguaje en local. Además, adquirí **Private LLMs**, una app premium que promete gestionar modelos de lenguaje privados con mayor facilidad. Aunque aún no la he probado a fondo, su adquisición forma parte de mi plan a futuro para evaluar soluciones avanzadas de LLMs en local.

---

## Probando Retrieval-Augmented Generation (RAG)

Una de las funcionalidades más interesantes de LM Studio es su capacidad de **Retrieval-Augmented Generation (RAG)**, que permite a los modelos de lenguaje mejorar sus respuestas utilizando información de documentos adjuntos. Para probar esta característica:

1. **Cargué varios documentos** con información relevante para que el modelo pudiera acceder a ellos.
2. **Realicé consultas específicas**, verificando que el modelo utilizara los documentos como fuente de referencia en sus respuestas.
3. **Evalué la precisión de la recuperación**, comparando respuestas con y sin RAG habilitado.

El rendimiento fue bastante bueno, con el modelo proporcionando respuestas más informadas y contextualizadas cuando el sistema RAG estaba activado. Esto representa una ventaja significativa para la personalización de LLMs en entornos privados.

---

## Convertir LM Studio en un Servidor API

Uno de mis objetivos principales era configurar **LM Studio** como un servidor API, utilizando el modelo **Phi-4 Q_8bits (14,6GB)**. Para ello, seguí los siguientes pasos:

1. **Habilitación de la API**: Activé la opción de servidor API en la configuración de LM Studio, lo que permite interactuar con los modelos desde otras aplicaciones.
2. **Verificación del acceso**: Utilicé herramientas como `curl` y Postman para confirmar que la API respondía correctamente.

El resultado fue positivo: LM Studio funcionaba perfectamente como un servidor API, lo que abre múltiples posibilidades para su integración en aplicaciones distribuidas.

---

## Configuración para Uso en Red Local

Para llevar las pruebas un paso más allá, decidí conectar una aplicación web, alojada en otro equipo de mi red doméstica, a la API de LM Studio. El proceso incluyó:

1. **Configuración de CORS y accesibilidad en red local**, para que otras máquinas en mi red pudieran hacer peticiones a la API sin restricciones.
2. **Configuración del frontend**, para realizar peticiones a la API de LM Studio.
3. **Manejo de CORS** en la aplicación web, para garantizar que las solicitudes fueran aceptadas sin restricciones.
4. **Pruebas de interacción** con la API, evaluando latencia y calidad de las respuestas.

El resultado fue interesante: la aplicación web pudo comunicarse con el modelo alojado en LM Studio sin problemas, demostrando que los LLMs en local pueden integrarse fácilmente con aplicaciones distribuidas sin necesidad de depender de servicios en la nube.

---

## Conclusión

Esta experiencia reforzó la viabilidad de ejecutar modelos de lenguaje en local como alternativa a las soluciones en la nube. La combinación de **LM Studio, RAG y una API accesible en red** ofrece una solución potente para arquitectos y desarrolladores que buscan mayor control sobre sus modelos de IA.

Próximamente, exploraré más a fondo el uso de **Private LLMs** y cómo optimizar la carga y gestión de documentos en entornos de producción.

¿Has probado LM Studio o algún otro LLM en local? ¡Comparte tu experiencia en los comentarios!

---


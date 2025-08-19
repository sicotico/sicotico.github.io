---
layout: post
title:  "Integración de Ollama con GitHub Copilot en Visual Studio Code: Guía Completa"
date:   2025-09-15 12:00:00 -0500
categories: desarrollo ia github-copilot ollama
---

# Integración de Ollama con GitHub Copilot en Visual Studio Code: Guía Completa

---

## Introducción

La integración de **Ollama** con **GitHub Copilot** en **Visual Studio Code (VS Code)** marca un hito para los desarrolladores que buscan combinar la flexibilidad de modelos de inteligencia artificial locales con la potencia de un asistente de codificación en la nube. Desde **abril de 2025**, GitHub Copilot soporta oficialmente la integración con Ollama, permitiendo a los usuarios aprovechar modelos locales directamente desde el chat de Copilot en VS Code. Esto no solo mejora la privacidad y el control sobre los datos, sino que también abre nuevas posibilidades para personalizar y optimizar el flujo de trabajo de desarrollo.

---

## ¿Qué es Ollama y GitHub Copilot?

### Ollama
Ollama es una herramienta que permite ejecutar modelos de lenguaje grandes (LLM) de forma local, facilitando su integración en entornos de desarrollo. Es ideal para desarrolladores que prefieren mantener sus datos y procesos de IA dentro de su infraestructura local, ya sea por privacidad, rendimiento o costos.

### GitHub Copilot
GitHub Copilot es un asistente de codificación basado en IA desarrollado por GitHub y OpenAI. Se integra directamente en editores como VS Code, Visual Studio, y JetBrains, ofreciendo sugerencias de código en tiempo real, explicaciones, y asistencia contextual. Copilot utiliza modelos avanzados de IA para entender el contexto del código y generar sugerencias relevantes.

---

## ¿Desde cuándo GitHub Copilot soporta Ollama?

La integración oficial de Ollama con GitHub Copilot se anunció en **abril de 2025**. Esta actualización permite a los usuarios seleccionar Ollama como proveedor de modelos dentro del chat de Copilot, lo que significa que ahora es posible utilizar modelos locales de Ollama directamente en el flujo de trabajo de desarrollo, sin depender exclusivamente de modelos en la nube.

---

## ¿Cómo funciona la integración?

### Paso 1: Configuración de Ollama
1. **Instalar Ollama**: Asegúrate de tener Ollama instalado y ejecutándose en tu máquina local o en un servidor accesible. Puedes descargar Ollama desde su [sitio oficial](https://ollama.ai/).
2. **Ejecutar un modelo**: Inicia un modelo de Ollama localmente. Por ejemplo:
   ```bash
   ollama serve
   ```
   Y luego carga el modelo que desees usar:
   ```bash
   ollama pull mistral
   ```

### Paso 2: Configuración en Visual Studio Code
1. **Instalar GitHub Copilot**: Asegúrate de tener la extensión de GitHub Copilot instalada en VS Code. Si aún no la tienes, puedes instalarla desde el [Marketplace de VS Code](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot).
2. **Seleccionar Ollama como proveedor**:
   - Abre el chat de GitHub Copilot en VS Code.
   - Haz clic en el selector de modelos (model picker).
   - Ve a **Manage Models** (Administrar modelos).
   - Selecciona **Ollama** como proveedor.
   - Si Ollama está ejecutándose localmente, Copilot detectará los modelos disponibles y te permitirá elegir uno.

### Paso 3: Configuración avanzada (Dev Containers)
Si trabajas en un **Dev Container**, necesitarás redirigir el tráfico de Ollama desde el contenedor a tu máquina host. Esto se puede lograr usando herramientas como `socat` o configurando el endpoint de Ollama en la configuración de VS Code Insiders:
```json
"github.copilot.chat.byok.ollamaEndpoint": "http://host.docker.internal:11434"
```
Esta configuración permite que el chat de Copilot se comunique con Ollama fuera del contenedor.

---

## Beneficios de la integración

- **Privacidad y control**: Al usar modelos locales, los datos sensibles nunca salen de tu entorno de desarrollo.
- **Personalización**: Puedes elegir entre una amplia variedad de modelos de Ollama, optimizados para diferentes tareas y lenguajes de programación.
- **Flexibilidad**: Ideal para entornos con restricciones de conectividad o políticas de privacidad estrictas.
- **Rendimiento**: Reduce la latencia al evitar la dependencia de servicios en la nube.

---

## Casos de uso

1. **Desarrollo local seguro**: Ideal para proyectos que manejan datos sensibles o código propietario.
2. **Entornos sin conexión**: Permite seguir utilizando asistencia de IA incluso sin acceso a internet.
3. **Experimentos con modelos**: Facilita probar diferentes modelos de Ollama sin cambiar de entorno.
4. **Educación y formación**: Útil para enseñar o aprender sobre IA y desarrollo de software en un entorno controlado.

---

## Limitaciones y consideraciones

- **Requisitos técnicos**: Necesitas tener Ollama instalado y configurado correctamente, lo que puede requerir conocimientos técnicos adicionales.
- **Rendimiento del hardware**: Ejecutar modelos locales puede consumir recursos significativos de CPU y RAM.
- **Compatibilidad**: Actualmente, esta funcionalidad está disponible para usuarios de GitHub Copilot Free y Pro, pero es importante verificar las actualizaciones oficiales para cambios en los planes de suscripción.

---

## Conclusión

La integración de Ollama con GitHub Copilot en VS Code es un avance emocionante que combina lo mejor de ambos mundos: la potencia de la IA local y la conveniencia de un asistente de codificación en la nube. Con esta integración, los desarrolladores pueden personalizar su experiencia de desarrollo, mejorar la privacidad y optimizar su flujo de trabajo como nunca antes.

Si aún no has probado esta integración, ¡ahora es el momento perfecto para empezar! Configura Ollama, selecciona tus modelos favoritos y lleva tu productividad al siguiente nivel con GitHub Copilot.

---

**¿Ya has probado la integración de Ollama con GitHub Copilot? ¡Cuéntanos tu experiencia en los comentarios!**

---

### Recursos adicionales
- [Documentación oficial de GitHub Copilot](https://docs.github.com/copilot)
- [Guía de Ollama](https://ollama.ai/)
- [Configuración avanzada en Dev Containers](https://www.returngis.net/2025/04/🚀-como-usar-tus-modelos-de-ollama-🦙-en-github-copilot-chat/)

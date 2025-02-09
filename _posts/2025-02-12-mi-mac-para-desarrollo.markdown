---
layout: post
title:  "Mi mac para desarrollo Contenedores vs Virtualización"
date:   2025-02-12 10:57:08 +0200
tags: [Mac]
---

# Preparando un Mac para Desarrollo: Contenedores vs Virtualización

Como arquitecto de cloud con experiencia en infraestructura y plataformas, últimamente he estado explorando proyectos de desarrollo para comprender mejor las necesidades de los usuarios. Ayer fue un día particularmente intenso, dedicado a preparar mi Mac para pruebas con modelos de lenguaje, virtualización y herramientas de automatización. Aquí comparto mi experiencia.

## Índice

1. [Introducción](#introducción)
2. [Máquinas Virtuales y Virtualización](#máquinas-virtuales-y-virtualización)
   - [UTM y Vagrant: Problemas de Compatibilidad](#utm-y-vagrant-problemas-de-compatibilidad)
   - [Creación de Máquinas Virtuales](#creación-de-máquinas-virtuales)
   - [Windows 11 en VM](#windows-11-en-vm)
   - [Ubuntu Server en VM](#ubuntu-server-en-vm)
3. [Contenedores y Dev Containers](#contenedores-y-dev-containers)
   - [Introducción a Dev Containers](#introducción-a-dev-containers)
   - [Experiencia con ChatGPT y Dev Containers en VSCode](#experiencia-con-chatgpt-y-dev-containers-en-vscode)
   - [Comparación entre VMs y Dev Containers](#comparación-entre-vms-y-dev-containers)
4. [PowerShell en macOS: ¿Realmente lo Necesitaba?](#powershell-en-macos-realmente-lo-necesitaba)
5. [Gestión de Homebrew y Python en macOS](#gestión-de-homebrew-y-python-en-macos)
6. [Limpieza y Restauración de macOS](#limpieza-y-restauración-de-macos)
7. [Reflexión Final: ¿Vale la Pena Todo Esto?](#reflexión-final-vale-la-pena-todo-esto)

## Máquinas Virtuales y Virtualización

### UTM y Vagrant: Problemas de Compatibilidad

Actualicé **UTM**, una herramienta open-source de virtualización para macOS basada en QEMU, porque buscaba una solución eficiente para ejecutar máquinas virtuales en mi entorno. También instalé **Vagrant** para automatizar la gestión de máquinas virtuales, ya que en el pasado lo había utilizado en entornos de desarrollo de WordPress. Sin embargo, al probarlo en este contexto, encontré problemas de compatibilidad con UTM y noté que su configuración no era tan intuitiva como esperaba, lo que me llevó a reconsiderar su uso.

### Creación de Máquinas Virtuales

Como ya tenía Docker Studio y UTM, probé Vagrant, pero me dio problemas de compatibilidad con UTM y no lo vi como algo interesante para mi objetivo, que era desarrollar una aplicación en Python. Al final, decidí crear VMs manualmente para clonarlas y usarlas cuando fueran necesarias. Creé dos entornos:

- **Windows 11**: Luego de clonar la VM, apliqué un Playbook para deshabilitar configuraciones innecesarias, incluido el antivirus, ya que buscaba maximizar el rendimiento. No tenía forma de conseguir una versión LTSC, lo que habría sido ideal para reducir aún más los procesos en segundo plano y mejorar la estabilidad del sistema. Además, ajusté algunas configuraciones de sistema para minimizar el consumo de recursos.
- **Ubuntu Server**: Opté por esta versión porque era la opción más fácil y optimizada para ejecutarse en QEMU. Intenté usar Apple Native Virtualization, pero se me atrancó un poco, así que lo dejaré para un artículo futuro cuando logre que funcione.

## Contenedores y Dev Containers

### Introducción a Dev Containers

A pesar de mis esfuerzos en la virtualización, terminé dándome cuenta de que **ya casi no uso máquinas virtuales para desarrollo**. En cambio, enfoqué mi atención en **Dev Containers**, un concepto en el que un entorno de desarrollo se ejecuta en un contenedor Docker, ofreciendo una mayor portabilidad y consistencia.

### Experiencia con ChatGPT y Dev Containers en VSCode

Utilicé ChatGPT para generar un archivo `.devcontainer.json`, pero contenía configuraciones incorrectas. Finalmente, recurrí al video de ReturnGIS y usé la opción integrada de VSCode para generar el archivo automáticamente. Esto me permitió obtener una configuración funcional sin tantas complicaciones.

## PowerShell en macOS: ¿Realmente lo Necesitaba?

Decidí instalar **PowerShell en macOS** para evaluar su utilidad en mi flujo de trabajo, pero en realidad solo lo utilizo para Azure. Luego me di cuenta de que no lo necesitaba, considerando que Azure ya proporciona entornos de PowerShell integrados.

## Gestión de Homebrew y Python en macOS

Mientras realizaba estos experimentos, accidentalmente desconfiguré la instalación de **Python** en macOS y descubrí que mi instalación de **Homebrew** estaba en una ruta no estándar. Esto se debió a que usaba **AppLite** para gestionar Homebrew, permitiéndole modificar su ubicación. 

### Pasos para restaurar Homebrew y Python

1. **Exportar un listado de aplicaciones instaladas:**
   - Generé un listado de las aplicaciones instaladas tanto en formato fórmula como en cask.
2. **Ejecutar un script para desinstalar todas las aplicaciones:**
   - Utilicé un script que eliminó todas las aplicaciones junto con sus recursos y dependencias.
3. **Eliminar completamente Homebrew:**
   - Adapté el script oficial de desinstalación de Homebrew y lo ejecuté para remover cualquier rastro de la instalación anterior.
4. **Reinstalar Homebrew de manera oficial:**
   - Seguí el método recomendado utilizando `curl + script` para reinstalarlo en la ruta estándar.

Este proceso me llevó a una conclusión clave: **las máquinas virtuales y los contenedores son herramientas maravillosas para evitar tocar configuraciones a nivel del sistema operativo**.

## Reflexión Final: ¿Vale la Pena Todo Esto?

Después de experimentar con diversas herramientas, llegué a la conclusión de que, para mi flujo de trabajo, los **Dev Containers** son la opción más eficiente en términos de rapidez y portabilidad. Aunque las máquinas virtuales siguen siendo una alternativa viable para ciertos casos, su tiempo de arranque y consumo de recursos las hacen menos atractivas en comparación.

Por otro lado, herramientas como **PowerShell en macOS** y la gestión de **Homebrew** requieren una evaluación más detallada antes de adoptarlas en el día a día. En retrospectiva, evitaría instalar PowerShell en macOS y gestionaría mejor la ubicación de Homebrew para evitar conflictos. En el futuro, priorizaré soluciones que ofrezcan una mayor integración con mis necesidades sin comprometer la eficiencia del sistema.

### Ideas clave:

- Los modelos de lenguaje en local pueden ser una alternativa interesante, pero requieren una infraestructura optimizada.
- PowerShell en macOS es útil en casos específicos, pero poco necesario si ya trabajas con Azure.
- La virtualización sigue siendo valiosa en ciertos escenarios, pero **Dev Containers están desplazando el uso de VMs en entornos de desarrollo**.
- Mantener un entorno limpio y ordenado en macOS es clave para evitar problemas inesperados.


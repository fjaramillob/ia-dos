# Fuentes de verdad

IA-DOS evita mantener la misma información manualmente en varios lugares.

Cada tipo de información debe tener una ubicación principal definida por el proyecto.

## Mapa genérico

| Información | Fuente de verdad recomendada |
|---|---|
| Propósito, usuarios y alcance | memoria durable del proyecto |
| Estado actual conocido | memoria durable actualizada con evidencia |
| Arquitectura vigente | registro arquitectónico o memoria durable |
| Decisiones durables | registro de decisiones adoptado por el proyecto |
| Organización conversacional | configuración documentada del entorno conversacional |
| Instrucciones del orquestador | artefacto de orquestación adoptado |
| Instrucciones para coding agents | archivo, configuración o política adoptada por el entorno |
| Trabajo pendiente | sistema de seguimiento elegido por el proyecto |
| Alcance de un plan | `Planning Task` |
| Propuesta de implementación | `Implementation Plan` |
| Alcance de una ejecución | `Execution Task` |
| Implementación | artefactos reales del producto |
| Evidencia de ejecución | `Execution Report`, revisión o mecanismo equivalente |
| Estándar común | fuente canónica de IA-DOS |

Los nombres de herramientas concretas pueden usarse como parámetros del proyecto, pero no son requisitos del método.

## Autoridad por ámbito

Una fuente no es canónica para todo.

Ejemplos:

- la memoria puede gobernar decisiones aceptadas, pero no demostrar que el código existe;
- la implementación demuestra estado real, pero no necesariamente explica por qué se tomó una decisión;
- un reporte demuestra acciones y verificaciones, pero no reemplaza el artefacto modificado;
- una referencia histórica aporta aprendizaje, pero no gobierna automáticamente el proyecto actual.

Consulta `docs/execution/source-and-artifact-authority.md`.

## Conversaciones

Las conversaciones sirven para explorar, coordinar, decidir y preparar trabajo.

No son una fuente de verdad durable.

Cuando una conversación produce una decisión, restricción, cambio de alcance o información que debe conservarse, el resultado debe registrarse en la fuente canónica correspondiente.

## Planificación

Un `Implementation Plan` es una propuesta técnica revisable.

No constituye:

- estado implementado;
- autorización de ejecución;
- evidencia de que los recursos existen;
- decisión durable hasta ser aceptado y registrado donde corresponda.

## Contradicciones

Cuando dos fuentes se contradicen:

1. identifica el ámbito exacto del conflicto;
2. determina qué fuente tiene autoridad para ese ámbito;
3. distingue estado real, decisión, propuesta y evidencia;
4. corrige o marca como obsoleta la fuente secundaria;
5. registra la resolución en la memoria durable cuando corresponda.

El Cycle Owner resuelve contradicciones dentro de su dominio. `00` interviene cuando el conflicto es transversal o estratégico.

## Regla

Los documentos pueden enlazarse entre sí, pero no deben copiarse completos sin una razón clara.

La autoridad debe declararse explícitamente; no se infiere solo por el nombre, formato, ubicación o herramienta que contiene la información.
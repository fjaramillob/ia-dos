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
| Evidencia de ejecución | `Execution Report`, diff, revisión o mecanismo equivalente |
| Historial operacional de archivos intercambiados | Exchange, cuando el proyecto lo adopta |
| Estándar común | fuente canónica de IA-DOS |

Los nombres de herramientas concretas pueden usarse como parámetros del proyecto, pero no son requisitos del método.

## Autoridad por ámbito

Una fuente no es canónica para todo.

Ejemplos:

- la memoria durable puede gobernar decisiones aceptadas, pero no demostrar que el código existe;
- la implementación demuestra estado real, pero no necesariamente explica por qué se tomó una decisión;
- un reporte aporta evidencia de acciones y verificaciones, pero no reemplaza el artefacto modificado;
- Exchange conserva qué archivos fueron enviados y recibidos, pero no reemplaza estado vigente, backlog, implementación o decisiones;
- una referencia histórica aporta aprendizaje, pero no gobierna automáticamente el proyecto actual.

Consulta `docs/execution/source-and-artifact-authority.md`.

## Conversaciones

Las conversaciones sirven para explorar, coordinar, decidir y preparar trabajo.

No son una fuente de verdad durable.

Cuando una conversación produce una decisión, restricción, cambio de alcance o información que debe reutilizarse, el resultado se registra en la fuente durable correspondiente cuando sea necesario.

## Exchange

Exchange es una pasarela pasiva y opcional de archivos Markdown.

Puede conservar los archivos que se intercambiaron para responder preguntas como:

> ¿Qué archivo se envió y qué archivo volvió?

Exchange no define el significado de esos archivos, no crea artefactos, no genera IDs, no mantiene backlog y no consolida memoria durable.

Cuando un hecho observado en un `Execution Report` merece persistirse, esa evaluación ocurre después de revisar la evidencia. Si corresponde actualizar memoria durable, se hace mediante una acción o tarea documental explícitamente autorizada.

## Planificación

Un `Implementation Plan` es una propuesta técnica revisable.

No constituye:

- estado implementado;
- autorización de ejecución;
- evidencia de que los recursos existen;
- decisión durable hasta ser aceptado y registrado donde corresponda.

## Ejecución

Una `Execution Task` conserva el alcance autorizado aunque se transporte por conversación, archivo, issue o Exchange.

El mecanismo de almacenamiento no cambia la autoridad del artefacto ni permite omitir permisos, límites o criterios necesarios para ejecutar de forma segura.

El `Execution Report` conserva evidencia de ejecución. No aprueba su propio resultado, no selecciona la decisión de gobierno posterior y no funciona como mecanismo de consolidación de memoria.

## Contradicciones

Cuando dos fuentes se contradicen:

1. identifica el ámbito exacto del conflicto;
2. determina qué fuente tiene autoridad para ese ámbito;
3. distingue estado real, decisión, propuesta, evidencia e historial;
4. corrige o marca como obsoleta la fuente secundaria;
5. registra la resolución en memoria durable cuando deba reutilizarse.

El Cycle Owner puede resolver contradicciones dentro de la autoridad delegada de su dominio. La persona responsable conserva la aprobación final cuando la resolución cambia dirección, autoridad, riesgo o impacto relevante. `00` interviene cuando el conflicto requiere reorientación transversal.

## Regla

Los documentos pueden enlazarse entre sí, pero no deben copiarse completos sin una razón clara.

La autoridad debe declararse explícitamente; no se infiere sólo por el nombre, formato, ubicación o herramienta que contiene la información.

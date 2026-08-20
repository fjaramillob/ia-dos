# Terminología

IA-DOS mantiene en inglés algunos términos técnicos ampliamente utilizados, pero los explica en español.

## `Project Orchestrator`

Asistente conversacional utilizado para dirigir y coordinar el proyecto desde ChatGPT, Gemini, Claude u otro entorno equivalente.

Comprende el contexto, enruta decisiones, prepara tareas, selecciona contexto y revisa el retorno de los coding agents.

## `Conversation Space`

Conversación persistente dedicada a un dominio de gobierno del proyecto, por ejemplo dirección, producto, arquitectura, operación o memoria.

No es una etapa obligatoria ni una fuente de verdad independiente. Sus resultados durables deben registrarse en la fuente canónica correspondiente.

## `Cycle Owner`

Conversation Space que gobierna un resultado mientras éste permanezca dentro de su dominio.

Mantiene objetivo y límites, prepara o valida tareas, revisa retornos y decide cierre, corrección, transferencia o escalamiento.

## coding agent

Herramienta con capacidad de inspeccionar y, cuando está autorizado, modificar artefactos reales del proyecto.

Puede actuar bajo roles distintos, por ejemplo `Coding Agent — Planning` o `Coding Agent — Execution`.

## `Planning Task`

Artefacto de solo lectura que delimita una incertidumbre técnica o inspección necesaria antes de ejecutar.

Produce un `Implementation Plan`. No autoriza cambios físicos.

## `Implementation Plan`

Propuesta técnica producida a partir de una Planning Task.

Describe evidencia, decisión recomendada, estrategia mínima y una primera unidad candidata. No equivale a ejecución autorizada ni a estado implementado.

## `Execution Task`

Contrato semántico de una unidad concreta, acotada, verificable y terminable dirigida a `Coding Agent — Execution`.

Declara objetivo, alcance, autoridad, permisos, criterios, verificaciones, condiciones de detención y destino del reporte. El mecanismo usado para almacenarla o transportarla no cambia este contrato.

## `Execution Cell`

Contexto durable de ejecución definido por proyecto cuando mantener un flujo separado mejora la continuidad operacional.

Una Execution Cell no es una tarea, una profesión ni un Conversation Space. Cuando la herramienta permite conversaciones persistentes, una conversación activa puede representar una instancia de la célula y reutilizarse mientras siga respondiendo bien.

## `Execution Report`

Artefacto de retorno que describe resultado, cambios, verificaciones, evidencia, desviaciones y pendientes de una Execution Task.

El estado del reporte describe la ejecución; la decisión posterior pertenece al Cycle Owner.

## `Exchange Protocol v0`

Perfil opcional de identificación, persistencia y transporte para conservar `TASK` y `REPORT` fuera de las conversaciones.

No crea un tipo nuevo de Execution Task o Execution Report y no sustituye memoria, implementación ni backlog.

## `Task ID`

Identificador de una tarea o intercambio.

Puede seguir el esquema clásico adoptado por el proyecto o, en Exchange v0, usar un identificador autocontenido como:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

## `Cycle ID`

Identificador opcional de un ciclo de trabajo cuando el proyecto utiliza ese esquema.

Exchange v0 no exige inventar un Cycle ID: puede declararse `NO APLICA`.

## memoria durable / LLM Wiki

Base de conocimiento que conserva estado, decisiones y contexto reusable del proyecto.

Puede materializarse en Markdown, documentación versionada u otro mecanismo definido por el proyecto. No demuestra por sí sola que una implementación exista.

## `Context Pack`

Conjunto pequeño de documentos o rutas seleccionados para entregar a un asistente o agente solo el contexto necesario.

Es una técnica posible de compresión de contexto, no una estructura obligatoria de toda memoria durable.

## `CORE`

Context Pack transversal utilizado por proyectos que adoptan ese patrón.

Puede contener propósito, estado resumido, restricciones, decisiones vigentes y ubicación de fuentes de verdad. No es un requisito universal de IA-DOS.

## `Referencias Wiki`

Rutas de memoria durable relacionadas con una tarea para trazabilidad o navegación.

Una referencia no implica que el coding agent deba leerla.

## `Lectura requerida`

Lista explícita de documentos que el coding agent debe consumir antes de actuar.

Se utiliza deliberadamente cuando la lectura directa aporta precisión real y no debe confundirse con referencias opcionales.

## `repository`

Repositorio versionado donde se almacena código, documentación u otros archivos de un proyecto.

## `branch`

Línea de trabajo separada dentro de Git. Permite realizar cambios sin modificar directamente la versión principal.

## `commit`

Registro versionado de uno o más cambios relacionados.

## `issue`

Elemento utilizado para registrar trabajo pendiente, bugs, propuestas o preguntas dentro de una plataforma de seguimiento.

## `pull request`

Solicitud para revisar e incorporar cambios desde una branch antes de agregarlos a la versión principal.

## `AGENTS.md`

Archivo que entrega instrucciones persistentes a los agentes que trabajan dentro de un repositorio.

## handoff

Traspaso estructurado entre roles o espacios. Puede transferir una decisión de dominio, una tarea o un artefacto de retorno.

## `guardrail`

Límite o regla que impide acciones inseguras, fuera de alcance o no autorizadas.

## `Definition of Done`

Conjunto de condiciones que deben cumplirse antes de considerar terminado un trabajo.

## `workspace`

Entorno local o lógico que agrupa los recursos de uno o más proyectos.

IA-DOS puede recomendar una estructura, pero no exige una topología universal.

## app

Repositorio, carpeta o conjunto de artefactos que contiene la implementación ejecutable del proyecto.

## wiki

Nombre habitual para una materialización de la memoria durable del proyecto.

## Fuente de verdad

Ubicación canónica donde debe mantenerse un tipo determinado de información dentro de un ámbito concreto.

Una fuente puede ser autoritativa para decisiones y no para implementación, o viceversa.
# Terminología

Este glosario describe los términos operativos vigentes de IA-DOS y separa conceptos actuales de compatibilidad histórica.

## Persona responsable

Persona que mantiene la dirección del proyecto y conserva la aprobación final cuando una decisión cambia objetivo, autoridad, riesgo, coste, datos, seguridad o impacto relevante.

## `Project Orchestrator`

Asistente conversacional que integra dirección, contexto, fuentes y contratos para conducir el siguiente avance verificable. No sustituye a la persona responsable ni ejecuta cambios físicos por defecto.

## `Conversation Space`

Contexto conversacional persistente dedicado a un dominio de gobierno cuando separarlo mejora claridad o continuidad.

Los Conversation Spaces se abren bajo demanda. Sus números son identificadores, no fases obligatorias.

## `00 — Dirección y orquestación`

Conversation Space inicial canónico. Mantiene dirección transversal y recibe reorientaciones o escalamiento real; no funciona como dispatcher obligatorio.

## `Cycle Owner`

Conversation Space que gobierna un resultado mientras permanezca dentro de su dominio.

Mantiene objetivo y límites, prepara o valida artefactos y revisa retornos dentro de la autoridad delegada. La persona responsable conserva la aprobación final cuando corresponda.

## `Specialist Handoff`

Artefacto que transfiere una decisión o el gobierno de un resultado a otro Conversation Space. No autoriza ejecución técnica.

## memoria durable

Responsabilidad funcional de conservar conocimiento vigente y reusable fuera de conversaciones efímeras.

Puede materializarse mediante una LLM Wiki u otro mecanismo durable adecuado al proyecto.

## `LLM Wiki`

Término propio de IA-DOS para una materialización durable, portable y navegable de la memoria del proyecto para humanos y agentes.

Normalmente usa Markdown estándar cuando se implementa como base documental, pero no exige repositorio separado ni Obsidian.

## `Memory Bootstrap Gate`

Gate previo a una Planning Task o Execution Task que pregunta si la siguiente unidad depende de conocimiento relevante que sólo existe en conversaciones efímeras.

Resultados:

```text
PASS
BOOTSTRAP REQUIRED
```

No usa edad, cantidad de mensajes o número de tareas como umbral.

## checkpoint durable

Conjunto mínimo de conocimiento que debe persistirse cuando el Memory Bootstrap Gate devuelve `BOOTSTRAP REQUIRED`.

## `Contexto durable necesario`

Extracto mínimo de conocimiento estable que debe viajar dentro de una tarea porque el receptor lo necesita directamente.

## `Referencias Wiki`

Referencias de procedencia o navegación hacia la LLM Wiki. No implican lectura automática.

## `Lectura requerida`

Documentos concretos que el receptor debe consumir antes de actuar.

## `Planning Task`

Artefacto dirigido a `Coding Agent — Planning` para inspección y diseño técnico en solo lectura.

Produce `Implementation Plan` y no autoriza escritura.

## `Implementation Plan`

Propuesta técnica verificable resultante de una Planning Task. No equivale a implementación ni a autorización de ejecución.

## `Environment Preflight`

Artefacto de solo lectura usado cuando una Execution Task depende de una precondición indispensable del entorno que no está comprobada.

## `Environment Readiness Report`

Retorno del preflight con estados canónicos:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

Sólo `LISTO PARA EJECUCIÓN` permite aprobar o reanudar escritura.

## `Execution Task`

Contrato de una unidad de ejecución concreta, terminable y verificable. Declara objetivo, autoridad, alcance, permisos, criterios, verificaciones, condiciones de detención y destino del reporte.

Su semántica no cambia por transportarse mediante chat, archivo, issue o Exchange.

## `Execution Cell`

Contexto durable de ejecución definido por proyecto.

Puede reutilizar una misma conversación de coding agent entre múltiples tareas mientras siga respondiendo bien. No representa una tarea, especialidad profesional o Conversation Space. Los permisos no se acumulan entre tareas.

## `Execution Resume`

Artefacto que reanuda la misma Execution Task después de resolver un bloqueo, sólo si objetivo, alcance, autoridad, seguridad y arquitectura siguen sin cambios.

## `Execution Report`

Evidencia de lo ejecutado.

Estados canónicos:

```text
COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
```

Incluye `Atención requerida` cuando existe un bloqueo, riesgo, desviación o decisión concreta a revisar. No aprueba su propio resultado, no elige la siguiente unidad y no consolida memoria durable.

## `Exchange`

Pasarela pasiva y opcional de archivos Markdown entre Conversation Agents y Code Agents.

No define artefactos, IDs, nombres de archivo, templates, estados, permisos, workflow, backlog, memoria o decisiones.

Una topología posible es `inbox/`, `outbox/` y `archive/`; esas carpetas no son estados del método.

## `Task ID`

Identificador asignado por el Conversation Agent que construye una Execution Task. El Execution Report reutiliza ese ID por contrato.

Exchange no genera ni valida Task IDs.

## `Cycle ID`

Identificador opcional de un ciclo más amplio. Puede ser `NO APLICA` cuando el proyecto no necesita uno separado.

## `Coding Agent — Planning`

Rol técnico de solo lectura que inspecciona fuentes autorizadas y produce un Implementation Plan.

## `Coding Agent — Execution`

Rol técnico que materializa únicamente una Execution Task autorizada y produce un Execution Report.

## `Wiki Update Task`

Perfil documental de una `Execution Task` canónica utilizado cuando el resultado principal es modificar memoria durable Markdown.

No es un tipo de artefacto independiente.

## `Current Offline Pack`

Artefacto de distribución vigente para operar IA-DOS cuando el repositorio canónico no puede navegarse.

No es una segunda fuente de verdad y debe mantenerse sincronizado con los contratos actuales.

## Fuente de verdad

Recurso que tiene autoridad para un tipo de información dentro de un ámbito declarado.

No existe una fuente universal: implementación, memoria, evidencia, backlog y método pueden tener autoridades distintas.

## `AGENTS.md`

Archivo de instrucciones persistentes aplicables al recurso donde vive. No sustituye la LLM Wiki.

## handoff

Traspaso estructurado entre roles o espacios. Puede transferir una decisión de dominio, una tarea o un artefacto de retorno.

## guardrail

Límite que impide acciones inseguras, fuera de alcance o no autorizadas.

## `Definition of Done`

Conjunto de condiciones que deben cumplirse antes de considerar terminado un trabajo.

## workspace

Entorno local o lógico que agrupa recursos de uno o más proyectos. IA-DOS no exige una topología universal.

## Términos históricos o de compatibilidad

### `Context Pack`

Patrón usado en versiones anteriores para agrupar contexto. No forma parte del contrato mínimo vigente y no debe reintroducirse como requisito operativo. Un proyecto existente puede conservar un mecanismo similar si sigue aportando valor local.

### `CORE`

Nombre usado por starters antiguos de Wiki. No forma parte del Wiki Starter vigente.

### `Launch Mode`

Nombre utilizado durante una generación anterior del onboarding. Ya no es una fase ni un componente operativo: cuando la persona quiere avanzar, el Orchestrator aplica directamente los gates vigentes de memoria, readiness, Planning y Execution.

### `Exchange Protocol v0`

Nombre histórico reemplazado. El concepto vigente es simplemente `Exchange`, una pasarela pasiva de archivos sin protocolo semántico propio.

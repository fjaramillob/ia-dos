# Terminología

Este glosario describe los términos operativos vigentes de IA-DOS y separa conceptos actuales de compatibilidad histórica.

## Persona responsable

Persona que mantiene la dirección del proyecto y conserva la aprobación final aplicable. Interviene cuando una decisión cambia materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

## `Project Orchestrator`

Asistente conversacional que integra dirección, contexto, fuentes y contratos para conducir el siguiente avance verificable.

## `Conversation Space`

Contexto conversacional persistente dedicado a un dominio de gobierno cuando separarlo mejora claridad o continuidad. Se abre bajo demanda.

## `00 — Dirección y orquestación`

Conversation Space inicial canónico. Mantiene dirección transversal y recibe reorientaciones o escalamiento real; no funciona como dispatcher obligatorio.

## `Cycle Owner`

Conversation Space que gobierna un resultado mientras permanezca dentro de su dominio y autoridad delegada.

## `Specialist Handoff`

Artefacto que transfiere una decisión o el gobierno de un resultado a otro Conversation Space. Su transporte normativo es inline, autocontenido y copiable. No requiere `.md`, Exchange, path ni `Manual Artifact Launcher`.

## IA-DOS Alignment

Comprobación condicional de contratos vigentes cuando un Conversation Space es nuevo, se retoma después de un cambio relevante de IA-DOS o muestra reglas obsoletas.

No es un gate nuevo, no reinicia onboarding y no exige releer todo el framework.

## memoria durable

Responsabilidad funcional de conservar conocimiento vigente y reusable fuera de conversaciones efímeras.

## `LLM Wiki`

Posible materialización durable, portable y navegable de memoria del proyecto para humanos y agentes.

## `Memory Bootstrap Gate`

Gate que pregunta si la siguiente unidad depende de conocimiento relevante que sólo existe en conversaciones efímeras. Resultados: `PASS | BOOTSTRAP REQUIRED`.

## `Planning Task`

Artefacto dirigido a `Coding Agent — Planning` para inspección y diseño técnico en solo lectura respecto del proyecto/entorno inspeccionado. Produce `Implementation Plan`.

## `Implementation Plan`

Propuesta técnica verificable resultante de Planning. No equivale a implementación ni se autoaprueba.

El Cycle Owner puede adoptarlo dentro de autoridad delegada cuando no cambia materialmente la frontera reservada a la persona responsable.

## `Environment Preflight`

Artefacto de solo lectura usado cuando una Execution Task depende de una precondición indispensable no comprobada.

## `Environment Readiness Report`

Retorno del preflight: `LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO`.

## `Execution Task`

Contrato de un **outcome definido, cohesivo, acotado y verificable bajo una frontera estable de autoridad**.

No se divide sólo por duración, cantidad de archivos/comandos ni por fases internas de implementación, tests, commit, push, deploy o smoke.

## `Authority Envelope`

Sección semántica dentro de una Execution Task que agrupa permisos explícitos para el outcome completo.

No es un Artifact Type.

```text
acción sensible no declarada
→ no autorizada

acción declarada + gates cumplidos + frontera estable
→ puede ejecutarse dentro de la misma Task
```

## `Embedded Contract`

Parte de la autoridad que debe viajar dentro de la Task: outcome, scope, permisos, seguridad, criterios, verificaciones, stop conditions y entrega aplicable.

## `Required Reading`

Documentos concretos que el receptor debe leer antes de actuar.

## `Reference`

Referencia de autoridad, procedencia, trazabilidad o navegación. No implica lectura por defecto.

Una Task es suficientemente autocontenida cuando `Task + Required Reading` permiten ejecutarla sin depender de conversaciones previas.

## `Execution Cell`

Contexto de continuidad de ejecución definido por proyecto. Puede reutilizar una conversación entre múltiples Tasks sin heredar permisos.

## `Execution Checkpoint`

Sidecar operacional opcional `<TASK-ID>-CHECKPOINT.md` para tareas largas o cambio de Coding Agent.

Puede registrar avance, HEAD, worktree, fases completadas, pendiente y bloqueos.

No es Artifact Type ni autorización.

## `Execution Resume`

Reanuda la misma Task después de resolver un bloqueo sólo si objetivo, alcance, autoridad, seguridad y arquitectura siguen sin cambios.

```text
Execution Resume = Task original + delta del bloqueo resuelto
```

Conserva Task ID.

## `Execution Report`

Evidencia de lo ejecutado realmente. `Task = autorizado`; `Report = ocurrido`.

Estados: `COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO`.

Estructura preferente: `Outcome`, `Evidence`, `Actual Scope`, `Acceptance`, `Deviations`, `Final State`.

No aprueba su propio resultado, no elige siguiente unidad y no consolida memoria durable por defecto.

## `Exchange`

Pasarela opcional, provider-agnostic, filesystem-first y pasiva de artifacts Markdown hacia/desde Coding Agents.

```text
Exchange ≠ Google Drive
Exchange ≠ workflow engine
Exchange ≠ backlog
Exchange ≠ memoria durable
Exchange ≠ router entre Conversation Spaces
```

Puede usar Google Drive, OneDrive, Dropbox, Syncthing, NAS, carpeta local/manual u otro mecanismo equivalente como transporte físico.

Topología mínima:

```text
inbox/  = artifacts operativamente activos destinados a Coding Agents
outbox/ = outputs pendientes de consumo o aún requeridos por trabajo activo
archive/ = cold storage operacional por trazabilidad
```

`folder ≠ workflow state` y `archive ≠ aprobado/completado/memoria durable/repositorio de documentos vivos`.

## `Output Delivery`

Declaración opcional dentro de una Task que autoriza la materialización de su output expresamente indicado y sólo en el destino declarado.

## `Manual Artifact Launcher`

Prompt efímero y no autoritativo que localiza una Task ya construida y, cuando corresponde, el destino físico de su output.

No es un Artifact Type, no modifica la Task y no agrega autoridad.

## `Caveman Return`

Representación conversacional mínima de un output completo ya materializado. Sólo se usa cuando la Task declara `Caveman Return: Sí` y la materialización fue correcta.

## `Task ID`

Identificador asignado por el Conversation Agent que construye una Execution Task. El Report reutiliza ese ID.

## `Cycle ID`

Identificador opcional de un ciclo más amplio. Puede ser `NO APLICA`.

## `Coding Agent — Planning`

Rol técnico de solo lectura respecto del proyecto/entorno inspeccionado que produce Implementation Plan o comprueba readiness.

## `Coding Agent — Execution`

Rol técnico que materializa únicamente una Execution Task autorizada y produce Execution Report.

## `Wiki Update Task`

Perfil documental de una `Execution Task` canónica. No es un Artifact Type independiente.

## `Current Offline Pack`

Artefacto de distribución vigente para operar IA-DOS cuando el repositorio canónico no puede navegarse. Debe mantenerse sincronizado con los contratos actuales.

## Términos históricos o de compatibilidad

### `Context Pack`

Patrón anterior para agrupar contexto. No forma parte del contrato mínimo vigente.

### `CORE`

Nombre usado por starters antiguos de Wiki. No forma parte del Wiki Starter vigente.

### `Launch Mode`

Nombre histórico de una generación anterior del onboarding. Ya no es una fase operativa.

### `Exchange Protocol v0`

Nombre histórico reemplazado por `Exchange`, una pasarela pasiva sin protocolo semántico propio.
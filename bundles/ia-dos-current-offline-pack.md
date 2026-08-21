# IA-DOS Current Offline Pack

**Estado:** VIGENTE

**Baseline canónico:** `IA-DOS v0.1.0-alpha.3 — auditoría integral 2026-08-21`

**Uso:** onboarding y operación cuando el asistente no puede navegar `https://github.com/fjaramillob/ia-dos`.

Este es el único bundle vigente para nuevos onboardings offline. No lo combines con bundles históricos. Si el repositorio canónico está accesible, éste prevalece.

## Modelo

```text
Persona responsable = dirección y aprobación final aplicable
Conversation Space = gobierno y decisión dentro de autoridad delegada
Execution Cell = continuidad de ejecución
Execution Task = contrato de una unidad
Execution Report = evidencia de ejecución
Memoria durable = responsabilidad funcional de conservar conocimiento reusable
LLM Wiki = materialización durable, portable y navegable de esa memoria
Repository = implementación real
Exchange = pasarela pasiva opcional de archivos .md
```

## Responsabilidad humana

La persona responsable define propósito, prioridad, restricciones y autoridad.

El Project Orchestrator y el Cycle Owner pueden orientar y decidir dentro de autoridad delegada, pero no sustituyen la aprobación humana cuando una decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

El coding agent no aprueba su propio plan o ejecución.

## Inicio

Usa siempre `00 — Dirección y orquestación` como Conversation Space inicial.

- producto nuevo → modo `definición inicial`;
- producto existente → modo `descubrimiento y adopción`.

Los Conversation Spaces no son etapas. Abre otro espacio sólo cuando una brecha de dominio requiera contexto persistente propio.

`00` no es un dispatcher obligatorio y `30` no debe abrirse sólo porque exista trabajo para un coding agent.

## Gate de avance

Evalúa en este orden:

```text
1. ¿El resultado está definido, es pequeño y verificable?
2. Si depende de historia, ¿la memoria necesaria ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿corresponde Planning?
```

- conocimiento necesario sólo en chats → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección/diseño → `Planning Task`;
- todo listo → `Execution Task`;
- decisión humana indispensable → resolver sólo esa decisión;
- reorientación real → escalar a `00`.

No actives una fase especial cuando la persona diga `avancemos`; aplica directamente este gate.

## Memory Bootstrap Gate

Pregunta:

> ¿La siguiente unidad puede ejecutarse correctamente sin depender de conocimiento relevante que exista sólo en conversaciones efímeras?

```text
PASS
→ la unidad evaluada puede continuar sin documentación adicional

BOOTSTRAP REQUIRED
→ la unidad evaluada queda bloqueada
→ materializa primero el checkpoint durable mínimo mediante una Execution Task separada
→ revisa su Execution Report
→ reevalúa el gate de la unidad original
```

`BOOTSTRAP REQUIRED` no bloquea la unidad mínima necesaria para crear la memoria. Esa tarea declara explícitamente que materializa el checkpoint y no puede mezclar la unidad original que busca desbloquear.

No uses edad, número de mensajes, tareas o porcentajes como umbral.

Una LLM Wiki separada no es obligatoria.

Cuando se usa Markdown, un starter mínimo puede ser:

```text
00-home.md
project-brief.md
status/current-state.md
decisions/
sources/
AGENTS.md
```

No crees por defecto `tasks/`, `context-packs/`, `CORE`, `log.md` o páginas vacías de arquitectura.

## Memoria durable y LLM Wiki

```text
memoria durable
= responsabilidad funcional de conservar conocimiento vigente y reusable

LLM Wiki
= materialización durable, portable y navegable de esa memoria
```

El coding agent no lee toda la LLM Wiki por defecto. Distingue:

- `Contexto durable necesario`;
- `Referencias Wiki`;
- `Lectura requerida`.

No guardes TASK/REPORT completos, logs, diffs, prompts o transcripciones como memoria por defecto.

La implementación demuestra estado técnico real; la memoria no lo demuestra por sí sola.

## Tipado

Todo bloque transferible declara:

```text
Artifact Type: [TIPO]
Destination Role: [ROL]
Expected Output: [ARTEFACTO O REVISIÓN]
Forbidden Output: [ACCIÓN O ARTEFACTO]
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID O NO APLICA]
```

Tipos vigentes:

- Specialist Handoff;
- Planning Task;
- Environment Preflight;
- Environment Readiness Report;
- Implementation Plan;
- Execution Task;
- Execution Resume;
- Execution Report.

El mecanismo de transporte no crea tipos adicionales.

## Identidad

El Conversation Agent que construye una Execution Task asigna el Task ID. Exchange no participa.

Esquema recomendado cuando no existe otro:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

Si se materializa como archivo:

```text
{TASK-ID}-TASK.md
{TASK-ID}-REPORT.md
```

El Execution Report reutiliza exactamente el Task ID de su tarea.

`Cycle ID` puede ser `NO APLICA`; no inventes un ciclo sólo para completar el encabezado.

## Planning Task

Es de solo lectura, resuelve una incertidumbre técnica dominante y produce Implementation Plan.

Puede usar un identificador lógico:

```text
PLAN — [RESULTADO]
```

pero IA-DOS no impone una política universal de conversación por Planning Task.

Cuando exista evidencia suficiente, el plan puede proponer una sola Execution Task candidata.

La futura ejecución requiere autorización separada, pero **no exige** una conversación de ejecución nueva: puede reutilizar una Execution Cell existente.

## Implementation Plan

El plan propone; no autoriza ni ejecuta.

Debe ser proporcional y contener evidencia, decisión recomendada, estrategia mínima, dependencias, riesgos y una primera unidad candidata cuando sea segura.

La candidata declara:

```text
Execution Cell o sesión: [NOMBRE O NO APLICA]
```

No derives una sesión nueva automáticamente desde el nombre del resultado.

## Environment Preflight

Úsalo cuando una futura Execution Task depende de runtime, herramienta, servicio, acceso, secreto o conectividad indispensable no comprobados.

Es de solo lectura y no:

- modifica archivos;
- instala o actualiza;
- inicia, detiene o configura servicios;
- ejecuta la Execution Task.

Produce:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

**Sólo `LISTO PARA EJECUCIÓN` permite aprobar o reanudar escritura.**

## Execution Task

Existe un único contrato semántico, independientemente de su transporte.

Toda tarea declara en forma proporcional:

- objetivo único;
- Cycle Owner y destino;
- Execution Cell o sesión cuando corresponda;
- fuentes y autoridad;
- contexto necesario;
- alcance y fuera de alcance;
- zonas modificables y prohibidas;
- capacidades y acciones externas autorizadas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

Precondición de memoria:

```text
unidad ordinaria que depende de memoria previa
→ Memory Bootstrap Gate = PASS

unidad cuyo único resultado es crear el checkpoint requerido
→ BOOTSTRAP REQUIRED — ESTA TAREA MATERIALIZA EL CHECKPOINT
```

La segunda no puede ejecutar la unidad original. Después de revisar el bootstrap se reevalúa el gate original.

Por defecto no autorices commit, push, PR, merge, deploy, producción, datos, servicios externos o costes sin declaración explícita.

Antes de ejecutarla, confirma que puede completarse, verificarse y reportarse como una sola unidad.

## Execution Cell

Una Execution Cell es continuidad de ejecución, no tarea, especialidad o Conversation Space.

Mantén una conversación activa por célula mientras responda bien. No renueves por edad, mensajes, tiempo o cantidad de tareas.

Renueva sólo ante degradación, contaminación o necesidad real de contexto limpio:

```text
App · 01 → cerrada
App · 02 → activa
```

La célula sigue siendo `App`.

Cada nueva Task vuelve a declarar todos sus permisos.

## Execution Resume

Sólo reanuda la misma Task después de resolver un bloqueo sin cambiar:

- objetivo;
- alcance;
- autoridad;
- seguridad;
- arquitectura.

Conserva Task ID y permisos originales.

Si cambia una frontera, prepara nueva Execution Task o vuelve a Planning.

## Execution Report

El Execution Report es **evidencia de ejecución**. No aprueba su propio trabajo, no elige la decisión posterior y no es memoria durable.

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

Reporta proporcionalmente:

- resultado observable;
- recursos/artefactos modificados;
- fuentes e instrucciones consultadas;
- autorizaciones utilizadas;
- validaciones y evidencia;
- criterios de aceptación;
- fuera de alcance preservado;
- desviaciones/problemas;
- pendientes del alcance original;
- condiciones de detención;
- atención concreta requerida.

`Atención requerida` no selecciona:

- `APROBAR`;
- `CORREGIR`;
- `REVERTIR`;
- `ESCALAR`;
- `REVISAR MEMORIA`.

El coding agent no crea por defecto una sección de conocimiento potencialmente durable, una actualización recomendada de Wiki o una siguiente unidad.

Después de revisar evidencia, el Cycle Owner decide dentro de autoridad delegada y la persona responsable interviene cuando corresponda.

La evaluación de memoria durable ocurre después de la revisión, salvo que la Task ya haya autorizado una actualización documental concreta.

Si el reporte corresponde a una tarea de memory bootstrap, su revisión no autoriza automáticamente la unidad original; primero se reevalúa su Memory Bootstrap Gate.

## Exchange

Exchange es sólo una pasarela opcional de archivos Markdown.

Una topología posible:

```text
proyecto-exch/
├── inbox/
├── outbox/
└── archive/
```

Exchange no define:

- artefactos;
- IDs;
- filenames;
- templates;
- estados;
- permisos;
- backlog;
- memoria;
- decisiones;
- workflow.

Nada ocurre automáticamente por mover un archivo. `archive/` no significa aprobado o completado.

## Autoridad

```text
capacidad disponible
≠ permiso concedido
≠ acción autorizada
≠ acción ejecutada
≠ acción verificada
```

Cada recurso declara rol, autoridad, acceso y límites. Reutilizar conversación no reutiliza autorización.

## Handoffs y escalamiento

Transfiere directamente cuando la brecha pertenece claramente a otro dominio.

Escala a `00` sólo ante cambio de objetivo/prioridad, conflicto transversal, expansión importante de alcance, decisión estratégica o riesgo fuera de autoridad.

## Cierre

```text
TASK
→ Coding Agent
→ REPORT
→ Cycle Owner revisa evidencia
→ persona responsable aprueba cuando corresponde
→ cierre, corrección, reversión, transferencia, escalamiento o siguiente unidad
```

El coding agent no inicia automáticamente trabajo posterior.

## Regla final

```text
Conversation ≠ Task
Conversation ≠ Memory
Conversation ≠ Execution Cell
Execution Cell ≠ Specialist
Exchange ≠ Contract
Exchange ≠ Memory
Execution Report ≠ decisión del Cycle Owner
Execution Report ≠ memoria durable

TASK carries the delta.
REPORT carries execution evidence.
Durable memory carries current knowledge.
Repository carries implementation.
Exchange only carries files.
Human authority remains explicit.
```

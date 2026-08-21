# IA-DOS Current Offline Pack

**Estado:** VIGENTE

**Baseline canónico:** `IA-DOS alpha — Fase 6`

**Uso:** onboarding y operación cuando el asistente no puede navegar `https://github.com/fjaramillob/ia-dos`.

Este es el único bundle vigente para nuevos onboardings offline. No lo combines con bundles históricos. Si el repositorio canónico está accesible, éste prevalece.

## Modelo

```text
Conversation Space → gobierna y decide
Planning Task → inspección/diseño en solo lectura
Environment Preflight → comprueba readiness
Execution Task → unidad autorizada
Execution Cell → continuidad de ejecución
Execution Report → evidencia de ejecución
Memoria durable → conocimiento vigente
Exchange → pasarela pasiva de .md
Repositorio → implementación real
```

## Inicio

Usa siempre `00 — Dirección y orquestación` como espacio inicial.

- producto nuevo → modo `definición inicial`;
- producto existente → modo `descubrimiento y adopción`.

Conversation Spaces base: `00`, `10 — Producto y UX`, `20 — Arquitectura y stack`, `30 — Ejecución y desarrollo`, `40 — Calidad, seguridad y cumplimiento`, `50 — Operación y entrega`, `90 — Wiki y memoria`.

No son etapas. Abre otro espacio sólo cuando la brecha pertenezca a otro dominio y requiera contexto persistente propio.

El espacio que confirma el resultado se convierte en **Cycle Owner** y revisa sus retornos. `00` no es un dispatcher obligatorio.

## Gate de avance

Evalúa:

```text
1. ¿El resultado está definido, es pequeño y seguro?
2. Si depende de historia, ¿la memoria necesaria ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta diseño, ¿el coding agent puede proponer una primera unidad segura?
```

- todo listo → `Execution Task`;
- conocimiento necesario sólo en chats → `Memory Bootstrap Gate`;
- readiness desconocido → `Environment Preflight`;
- falta inspección/diseño → `Planning Task`;
- decisión humana indispensable → resolver sólo esa decisión;
- reorientación real → escalar a `00`.

## Memory Bootstrap Gate

Pregunta:

> ¿La siguiente unidad puede ejecutarse correctamente sin depender de conocimiento relevante que exista sólo en conversaciones efímeras?

```text
PASS → continúa
BOOTSTRAP REQUIRED → persiste primero el checkpoint durable mínimo
```

No uses edad, número de mensajes, tareas o porcentajes como umbral. Una Wiki separada no es obligatoria.

Cuando se usa Markdown, un starter mínimo puede ser:

```text
00-home.md
project-brief.md
status/current-state.md
decisions/
sources/
AGENTS.md
```

No crees por defecto `tasks/`, `context-packs/`, `CORE` o logs.

El coding agent no lee toda la Wiki por defecto. Distingue `Contexto durable necesario`, `Referencias Wiki` y `Lectura requerida`.

## Tipado

Todo bloque transferible declara:

```text
Artifact Type: [TIPO]
Destination Role: [ROL]
Expected Output: [ARTEFACTO O DECISIÓN]
Forbidden Output: [ACCIÓN O ARTEFACTO]
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID O NO APLICA]
```

Tipos principales: Specialist Handoff, Planning Task, Environment Preflight, Environment Readiness Report, Implementation Plan, Execution Task, Execution Resume y Execution Report.

## Identidad

El **Conversation Agent que construye la Execution Task** asigna el Task ID. Exchange no participa.

Esquema recomendado cuando no existe otro:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

Si se materializa como archivo:

```text
{ID}-TASK.md
{ID}-REPORT.md
```

El Report reutiliza exactamente el Task ID de la Task. `Cycle ID` puede ser `NO APLICA`.

## Planning Task

Es de solo lectura, resuelve una incertidumbre técnica dominante, produce Implementation Plan y vuelve al mismo Cycle Owner. No autoriza cambios, commits, despliegues, datos, costes o acciones externas.

Cuando haya evidencia suficiente, puede proponer una sola Execution Task candidata.

La política de persistencia/renovación de conversaciones de Planning permanece abierta y no se infiere desde Execution Cells.

## Environment Preflight

Se usa cuando una Execution Task depende de runtime, herramienta, servicio, acceso, secreto o conectividad no comprobados.

No modifica, instala, inicia ni configura. Produce:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

**Sólo `LISTO PARA EJECUCIÓN` permite aprobar o reanudar escritura.**

## Execution Task

Existe un único contrato semántico, independientemente de su transporte.

Toda Task declara en forma proporcional:

- objetivo único;
- Cycle Owner y destino;
- fuentes y autoridad;
- contexto necesario;
- alcance y fuera de alcance;
- zonas modificables/prohibidas;
- capacidades y acciones externas autorizadas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

Por defecto no autorices commit, push, PR, merge, deploy, producción, datos, servicios externos o costes sin declaración explícita.

Antes de aprobarla confirma que puede implementarse, verificarse y reportarse como una sola unidad.

## Execution Cell

Una Execution Cell es continuidad de ejecución, no tarea ni especialidad.

Mantén una sola conversación activa por célula mientras responda bien. No renueves por edad, mensajes o cantidad de tareas. Renueva sólo ante degradación, contaminación o necesidad real de contexto limpio.

```text
App · 01 → cerrada
App · 02 → activa
```

La célula sigue siendo `App`.

Una segunda Task reutiliza la misma célula cuando corresponda, pero vuelve a declarar todos sus permisos.

## Exchange

Exchange es sólo una pasarela opcional de archivos Markdown.

```text
proyecto-exch/
├── inbox/
├── outbox/
└── archive/
```

No define artefactos, IDs, filenames, templates, estados, permisos, backlog, memoria, decisiones ni workflow. Nada ocurre automáticamente por mover un archivo. `archive/` no significa aprobado.

## Execution Resume

Sólo reanuda la misma Task después de resolver un bloqueo **sin cambiar objetivo, alcance, autoridad, seguridad ni arquitectura**. Conserva Task ID y permisos originales.

Si cambia una de esas fronteras, crea nueva Execution Task o vuelve a Planning.

## Execution Report

El Execution Report es **evidencia de ejecución**. No aprueba su propio trabajo, no elige la decisión posterior y no es memoria durable.

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión y decisión del Cycle Owner
Forbidden Output: aprobar el propio resultado | iniciar otra unidad
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

`Atención requerida` no selecciona `APROBAR`, `CORREGIR`, `REVERTIR`, `ESCALAR` ni `REVISAR MEMORIA`.

Después de revisar la evidencia, el **Cycle Owner** toma la decisión de gobierno. Si aparecen hechos nuevos relevantes, también evalúa después si corresponde consolidarlos en memoria durable. El coding agent no crea por defecto una sección de “conocimiento potencialmente durable”.

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

Transfiere directamente cuando la brecha pertenece claramente a otro dominio. Escala a `00` sólo ante cambio de objetivo/prioridad, conflicto entre dominios, expansión importante de alcance, decisión estratégica o riesgo fuera de autoridad.

## Cierre

```text
TASK
→ Code Agent
→ REPORT
→ Cycle Owner revisa evidencia
→ decide cierre, corrección, reversión, escalamiento o siguiente unidad
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
Execution Report ≠ Decisión del Cycle Owner
Execution Report ≠ Memoria durable

TASK carries the delta.
REPORT carries execution evidence.
Durable memory carries current knowledge.
Repository carries implementation.
Exchange only carries files.
```

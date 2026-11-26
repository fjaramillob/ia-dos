# Auditoría integral del repositorio — 2026-11-25

**Estado:** VIGENTE AL INTEGRARSE C07  
**Baseline de entrada:** `main @ a1f19640d30a2eabb58b7d4d63075497e03e1ee6`  
**Ciclo:** `IA-DOS-METHOD-RESOLUTION-CONSISTENCY-C07`

## Propósito

Revisar IA-DOS de punta a punta después de C05/C06, detectar contradicciones entre contratos vigentes y dejar una única semántica operativa para:

- Direct Execution;
- gobierno conversacional on-demand;
- autoridad efectiva;
- versionado/adopción del método;
- entry modes y defaults de proyecto;
- prompts/templates copiables;
- memoria durable;
- workspace governance;
- distribución offline.

La revisión distingue contratos normativos vigentes de evidencia histórica fechada.

## Alcance

Se recorrió el árbol completo de `main` previo a C07:

```text
119 blobs
root
.github/
bundles/
docs/
prompts/
research/
templates/
```

Se revisaron especialmente:

- `AGENTS.md`;
- `ORCHESTRATOR.md`;
- README / docs index;
- foundations;
- execution;
- onboarding;
- prompts;
- templates;
- manifest de adopción;
- Current Offline Pack;
- Roadmap / Changelog;
- auditorías históricas;
- enlaces Markdown relativos.

Después de las correcciones se revalidaron todos los archivos modificados contra el árbol completo.

## Hallazgos

### C07-01 — Method Resolution ambiguo

`versioning.md` afirmaba que cada proyecto debía fijar una versión concreta de IA-DOS, mientras el flujo DIRECT y la operación cotidiana apuntaban a la fuente canónica vigente.

Esto dejaba sin contrato explícito dos necesidades válidas:

- proyectos que quieren incorporar el método actual automáticamente;
- proyectos que necesitan reproducibilidad mediante pin.

También dejaba abierta la posibilidad de interpretar un SHA pegado en un chat como un pin durable.

### C07-02 — Mode y policy mezclados

El contrato canónico definía:

```text
Execution Entry Mode:
ORCHESTRATED | DIRECT
```

pero el manifest de adopción declaraba:

```text
ORCHESTRATED | DIRECT | MIXED
```

La intención de `MIXED` era válida a nivel de proyecto, pero no como tercer modo de una ejecución concreta.

### C07-03 — Autoridad Task-only residual

Algunas superficies todavía representaban a `Execution Task` como única autoridad concreta de ejecución:

- `docs/execution/README.md`;
- `docs/execution/source-and-artifact-authority.md`;
- `docs/execution/execution-task-types.md`;
- `templates/AGENTS.template.md`.

Eso contradecía C06, donde DIRECT puede operar mediante `Effective Execution Contract` sin Task física cuando el contrato es suficientemente claro.

### C07-04 — Auditoría vigente desactualizada

La documentación seguía señalando la auditoría de 2026-10-26 / C04 como vigente, aunque C05 y C06 habían cambiado contratos transversales.

### C07-05 — QA no cubría resolución metodológica

Los checklists existentes cubrían ejecución adaptativa, memoria y Direct Execution, pero todavía no verificaban explícitamente:

- chat SHA ≠ durable pin;
- FOLLOW_CURRENT estable durante un outcome;
- Mode ≠ Entry Policy;
- prompts cotidianos sin SHA fijo.

## Correcciones

### Method Resolution Policy

Se formalizó:

```text
Method Resolution Policy:
FOLLOW_CURRENT | PINNED
```

#### FOLLOW_CURRENT

- resuelve la referencia canónica vigente al comienzo de un nuevo outcome/sesión relevante;
- mantiene ese snapshot metodológico estable durante la ejecución;
- vuelve a resolver antes del siguiente outcome relevante;
- una versión/SHA mencionada sólo en chat, prompt o reporte no constituye pin.

Default cuando no existe declaración durable:

```text
FOLLOW_CURRENT
```

#### PINNED

- exige una fuente durable de adopción;
- usa la versión/tag/commit declarada;
- cambia sólo mediante upgrade explícito;
- una referencia local más nueva o una mención conversacional no reemplazan el pin.

### Entry Mode vs Entry Policy

Por ejecución:

```text
Execution Entry Mode:
ORCHESTRATED | DIRECT
```

Preferencia durable del proyecto:

```text
Execution Entry Policy:
ORCHESTRATED_DEFAULT | DIRECT_DEFAULT | FLEXIBLE
```

`FLEXIBLE` no es un tercer mode.

### Effective authority

La autoridad concreta de una ejecución se expresa mediante:

```text
ORCHESTRATED
→ Execution Task

DIRECT
→ Effective Execution Contract
```

La autoridad sensible sigue requiriendo declaración explícita. Direct Execution no amplía permisos por ausencia de un archivo Task.

### Prompts operativos

El prompt canónico de DIRECT ahora resuelve primero Method Resolution Policy.

Regla:

> Los prompts operativos cotidianos no fijan un SHA de IA-DOS salvo reproducción histórica deliberada o cuando el propio proyecto ya adopta durablemente ese pin.

### Instalación local

Se separó explícitamente:

```text
actualizar 00-ia-dos
≠
cambiar automáticamente la versión adoptada por un proyecto PINNED
```

El SHA mostrado por `git rev-parse HEAD` es evidencia del estado local, no un pin de proyecto por sí mismo.

### QA

Se añadieron controles para impedir regresiones en:

- Method Resolution;
- Entry Mode / Entry Policy;
- pins accidentales;
- Task-only authority;
- Direct Execution;
- Current Offline Pack.

## Resultado de la auditoría

### Árbol pre-C07

```text
Blobs revisados: 119/119
Referencias específicas de proyectos en contratos genéricos: 0
Gates conversacionales obligatorios residuales detectados: 0
Execution Task física universal detectada por heurística inicial: 0
Pins SHA operativos en repo detectados: 0
Enlaces Markdown relativos rotos detectados: 0
Hallazgo semántico de Mode/Policy: 1
Hallazgo semántico Method Resolution: 1
Hallazgos Task-only authority por lectura profunda: 4 superficies
```

### Regresión C07

Los 22 archivos modificados antes de materializar esta auditoría fueron revalidados contra el árbol completo.

```text
OLD_MIXED_MODE: 0
OLD_ALWAYS_PIN: 0
OLD_NO_CURRENT: 0
TASK_ONLY_AUTHORITY: 0
TASK_ONLY_AGENT: 0
STALE_ALPHA6 vigente: 0
OPERATIONAL_SHA_PIN C06: 0
Enlaces relativos rotos en archivos modificados: 0
```

## Dictamen

```text
Conceptual Architecture         PASS
Method Resolution               PASS
Execution Entry Mode            PASS
Execution Entry Policy          PASS
Direct Execution                PASS
Effective Execution Authority   PASS
Human / Agent Governance        PASS
Adaptive Execution              PASS
Memory Stewardship              PASS
Workspace Governance            PASS
Templates / Prompts             PASS
Onboarding                      PASS
Current Offline Pack            PASS
Historical Isolation            PASS
Relative Link Integrity         PASS
Version Traceability            PASS

REPOSITORY CONSISTENCY
→ PASS AL INTEGRARSE C07
```

## Regla de continuidad

Después de C07:

```text
sin pin durable
→ FOLLOW_CURRENT
→ resolver IA-DOS al comenzar el outcome
→ mantener snapshot metodológico durante ese outcome
→ volver a resolver en el siguiente

pin durable
→ PINNED
→ conservar baseline hasta upgrade explícito
```

Un SHA presente sólo en una conversación nunca debe congelar accidentalmente el método.

Esta auditoría es evidencia de consistencia; la fuente canónica continúa siendo el repositorio IA-DOS.

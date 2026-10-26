# Auditoría integral del repositorio — 2026-10-26

**Estado:** VIGENTE AL INTEGRARSE PR #50  
**Baseline de entrada:** `main @ a078dc1b37c64002460a50842df697416532c14b`  
**Ciclo:** `IA-DOS-REPOSITORY-CONSISTENCY-C04`  
**PR de integración:** `#50 — IA-DOS C04: consistencia integral post-C03`

## Propósito

Comprobar IA-DOS como un sistema documental completo después de C03, con énfasis en que cualquier agente reciba la misma semántica vigente sin importar si entra por:

- `AGENTS.md`;
- README / Orchestrator;
- onboarding;
- prompts;
- templates;
- documentación de ejecución;
- documentación de memoria;
- Current Offline Pack;
- checklists y preguntas de validación.

La auditoría distingue deliberadamente contratos normativos vigentes de evidencia histórica fechada.

## Alcance

Se recorrió recursivamente el árbol completo del repositorio:

```text
115 blobs
root
.github/
bundles/
docs/
prompts/
research/
templates/
```

Se revisaron específicamente:

- gobierno humano, Conversation Spaces y Cycle Owner;
- Planning Task / Implementation Plan;
- Environment Preflight;
- Execution Task;
- Protected Invariants;
- Adaptation Authority;
- Protected Boundaries;
- Authority Envelope;
- Execution Resume;
- Execution Report;
- Memory Bootstrap Gate;
- Memory Policy;
- Memory Stewardship;
- Operational Baseline;
- `90 — Documentación y memoria`;
- LLM Wiki y current-state;
- Exchange;
- discoverability;
- versionado;
- distribución offline;
- templates y prompts copiables.

## Hallazgos de entrada

El baseline C03 tenía un núcleo conceptual consistente, pero existía drift transversal en superficies que podían modificar conducta.

### P1 — comportamiento de agentes

Se detectaron contratos pre-C03 activos en:

- `AGENTS.md`;
- `templates/project-instructions.template.md`;
- `templates/AGENTS.template.md`;
- `templates/execution-resume.template.md`;
- `templates/conversation-space-handoff.template.md`;
- rutas rápidas de onboarding/orquestación.

El riesgo era que distintos agentes aplicaran IA-DOS de forma diferente según la superficie leída.

### P1 — Planning / Preflight / Resume

Persistían heurísticas como:

```text
readiness desconocido → Preflight
falta inspección/diseño → Planning
Task original + delta del bloqueo resuelto
```

aunque C03 ya había establecido:

```text
Planning separado
→ decisión material todavía no resuelta

Environment Preflight separado
→ readiness previo a autoridad sensible
  | capacidad/readiness objeto de evaluación
  | actor/entorno distinto

Execution normal
→ Revalidate
→ planificación interna
→ repair-in-place / safe retry dentro de BOUNDED

Execution Resume
→ bloqueo externo o interrupción real
```

### P1 — memoria estructural

La semántica de `90` no estaba propagada de forma uniforme.

Existían simultáneamente:

- `90 — Wiki y memoria`;
- `90 — Documentación y memoria`;
- memoria dentro del outcome sin distinguir `LOCAL` de `90_STRUCTURAL`;
- enum de Durable Memory Impact sin `ROUTE_TO_90` en templates de adopción.

### P2 — QA y distribución

Los propios checklists todavía validaban heurísticas anteriores, por lo que el repositorio podía superar una revisión formal sin cumplir C03.

### P2 — versionado

Existía una colisión objetiva:

```text
Current Offline Pack
→ v0.1.0-alpha.4 = ejecución adaptativa / custodia estructural

ROADMAP
→ v0.1.0-alpha.4 = Portability and adoption quality — PLANIFICADO
```

### P2 — auditoría vigente

`docs/index.md` todavía presentaba la auditoría de 2026-08-21 como vigente pese a los cambios #47, #48 y #49.

## Correcciones C04

### Ejecución adaptativa

Se propagó de forma consistente:

```text
Outcome
+ Protected Invariants
+ Adaptation Authority
+ Protected Boundaries
+ Authority Envelope
+ Acceptance
```

`Adaptation Authority: BOUNDED` permite:

- planificación interna;
- debugging;
- repair-in-place;
- ajuste de pruebas;
- mecanismo técnicamente equivalente;
- safe retry sin side effects materiales.

No autoriza cambiar outcome, invariantes, fronteras ni capacidades sensibles.

### Planning

Planning separado queda reservado para una decisión material todavía no resuelta antes de escribir.

No se usa por defecto para:

- debugging;
- implementación ordinaria;
- selección entre runners/herramientas equivalentes;
- diseño técnico que puede resolverse dentro del outcome autorizado.

### Environment Preflight

Preflight separado queda reservado para:

- readiness que debe conocerse antes de conceder autoridad sensible;
- capacidad/readiness que es ella misma el objeto de evaluación;
- inspección que requiere otro actor o entorno.

El estado volátil ordinario se revalida dentro de Execution.

### Execution Resume

Se normalizó:

```text
Execution Resume
= Task original
+ delta del bloqueo externo o interrupción real resuelta
```

Sólo aplica si siguen estables:

- outcome;
- Protected Invariants;
- Protected Boundaries;
- scope;
- autoridad;
- seguridad;
- arquitectura.

Repair-in-place durante una Execution abierta no exige Resume.

### Memory Stewardship

Se propagó:

```text
Memory Stewardship:
LOCAL | 90_STRUCTURAL | NO APLICA
```

`LOCAL` cubre baseline y memoria estrecha no estructural.

`90_STRUCTURAL` cubre arquitectura, datos/source of truth, seguridad/autoridad, contratos cross-domain, capacidades mayores, gobernanza y reorganización relevante de memoria.

### 90 — Documentación y memoria

`90` queda definido como custodio de memoria estructural:

- no dispatcher;
- no aprobador técnico;
- no paso obligatorio de cada ejecución.

```text
outcome técnico
→ ROUTE_TO_90
→ Specialist Handoff inline
→ 90
→ NO UPDATE | CONSOLIDATE | MATERIALIZE NOW
→ Wiki Update Task si corresponde
→ UPDATED cuando la materialización termina correctamente
```

`ROUTE_TO_90` significa pendiente de custodia. No se emite de nuevo desde una Wiki Task ya gobernada por `90`.

### Wiki

Se reforzó:

```text
home / mapa
→ current-state compacto
→ página de dominio relevante
→ Task vigente
```

`current-state` es snapshot/índice operativo, no historial acumulativo.

### Exchange

Se preservó:

- opcional;
- provider-agnostic;
- filesystem-first;
- pasivo.

`inbox/` y `outbox/` deben permanecer como superficie activa escasa; artifacts consumidos, superseded o duplicados pueden salir a `archive/` sin que la carpeta determine estado o aprobación.

### Versionado

Se resolvió la colisión:

```text
v0.1.0-alpha.4
→ Adaptive execution and structural memory
→ ACTUAL

v0.1.0-alpha.5
→ Portability and adoption quality
→ PLANIFICADO
```

## Verificación post-corrección

Se ejecutó nuevamente un recorrido del árbol completo de C04.

Resultado:

```text
Blobs revisados: 115/115
Residuos normativos activos detectados: 0
Enlaces Markdown relativos rotos detectados: 0
Templates/prompts copiables con heurística pre-C03 detectados: 0
```

Las búsquedas de regresión cubrieron, entre otros:

- nombre anterior `90 — Wiki y memoria`;
- `Task original + delta del bloqueo resuelto`;
- enum antiguo de Durable Memory Impact;
- `readiness desconocido → Preflight`;
- `falta inspección/diseño → Planning`.

Los matches históricos permanecen permitidos únicamente donde cumplen función de evidencia fechada o bundles históricos expresamente marcados como no vigentes.

## Integridad histórica

No se reescribieron bundles históricos para simular el método actual.

Los artifacts históricos pueden conservar:

- nombres anteriores;
- sesiones anteriores;
- heurísticas reemplazadas;
- snapshots de contratos viejos.

Su valor es trazabilidad, no autoridad normativa.

## Dictamen

```text
Conceptual Architecture        PASS
Core Orchestrator Contract     PASS
Agent-facing Instructions      PASS
Planning/Preflight Semantics   PASS
Execution Resume Semantics     PASS
Memory Stewardship             PASS
90 Structural Custody          PASS
Templates / Prompts            PASS
Discoverability                PASS
Current Offline Pack           PASS
Version Traceability           PASS
Historical Isolation          PASS
Relative Link Integrity        PASS

REPOSITORY CONSISTENCY
→ PASS AL INTEGRARSE PR #50
```

## Regla de continuidad

Después de integrar PR #50, los agentes y Conversation Spaces que se retomen tras este cambio deben ejecutar **IA-DOS Alignment condicional**:

1. leer sólo los contratos vigentes necesarios;
2. actualizar conocimiento operativo desde `main`;
3. no reiniciar onboarding;
4. no reconstruir el proyecto desde chats;
5. preservar decisiones de proyecto ya aceptadas;
6. aplicar C03/C04 como semántica vigente.

La referencia canónica sigue siendo el repositorio `main`; esta auditoría es evidencia de consistencia, no una segunda fuente de verdad.

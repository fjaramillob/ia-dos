# Auditoría integral del repositorio — 2026-11-25 / C08

**Estado:** VIGENTE AL INTEGRARSE C08  
**Baseline de entrada:** `main @ b8f02c9687c3c7e50a1a3d42ef2fe1d1372797c2`  
**Ciclo:** `IA-DOS-DIRECT-ORCHESTRATED-CONSISTENCY-C08`

## Propósito

Revisar IA-DOS de punta a punta inmediatamente después de C07, contrastar la auditoría declarada con las superficies normativas reales y cerrar cualquier contradicción residual antes de volver a publicar `main`.

La revisión conserva evidencia histórica y corrige únicamente contratos vigentes, superficies copiables, onboarding, distribución offline y punteros de validación.

## Hallazgo principal

C07 formalizó correctamente:

```text
Method Resolution Policy
FOLLOW_CURRENT | PINNED

Execution Entry Mode
ORCHESTRATED | DIRECT

Execution Entry Policy
ORCHESTRATED_DEFAULT | DIRECT_DEFAULT | FLEXIBLE
```

y también estableció que DIRECT puede operar sin una `Execution Task` física cuando el `Effective Execution Contract` es reconstruible.

Sin embargo, la pasada C08 encontró residuos normativos que C07 no detectó:

1. varios gates genéricos seguían resolviendo `outcome definido → Execution Task` sin distinguir entry mode;
2. varias pruebas de continuidad exigían `Task vigente`, haciendo a DIRECT dependiente de un artefacto que el propio C07 declaró opcional;
3. `docs/getting-started/incorporate-existing-project-workspace.md` todavía exponía `ORCHESTRATED | DIRECT | MIXED` como `Execution Entry Mode`;
4. `Coding Agent — Execution` seguía definido como un rol que materializaba únicamente una Execution Task y producía siempre Execution Report;
5. el Current Offline Pack conservaba semántica Task-only en Authority Envelope, Memory Policy y su regla final;
6. README y onboarding todavía podían inducir a leer el flujo ORCHESTRATED como contrato universal.

Por lo tanto, el `PASS` de C07 fue útil como evidencia de esa pasada, pero tuvo falsos negativos. C08 no reescribe esa historia: la supera con una auditoría posterior.

## Corrección canónica

### Contrato de ejecución aplicable

```text
ORCHESTRATED
→ Execution Task

DIRECT
→ Effective Execution Contract
→ Direct Execution Gate
→ Task física sólo si aporta persistencia, handoff, autoridad sensible o trazabilidad
```

Los dos caminos comparten la misma frontera material:

- outcome;
- Protected Invariants;
- Adaptation Authority;
- Protected Boundaries;
- Authority Envelope;
- acceptance;
- stop conditions;
- Memory Policy / Stewardship cuando aplique.

La diferencia es la materialización del contrato, no la calidad ni la autoridad.

### Gates genéricos

Toda superficie genérica que antes decía:

```text
outcome definido
→ Execution Task
```

ahora debe interpretar:

```text
outcome definido
→ ORCHESTRATED: Execution Task + Revalidate
→ DIRECT: Effective Execution Contract + Direct Execution Gate
```

Una página que describe explícitamente una lane ORCHESTRATED puede seguir usando lenguaje Task-only dentro de esa frontera.

### Continuidad durable

La prueba de rehidratación deja de exigir `Task vigente` de forma universal:

```text
repositorio real
+ memoria durable relevante
+ contrato de ejecución aplicable
→ un Coding Agent nuevo puede orientarse
→ revalida la realidad antes de escribir
```

### Mode y policy

Se eliminó el residuo:

```text
Execution Entry Mode
ORCHESTRATED | DIRECT | MIXED
```

y se conserva:

```text
Execution Entry Mode
ORCHESTRATED | DIRECT

Execution Entry Policy
ORCHESTRATED_DEFAULT | DIRECT_DEFAULT | FLEXIBLE
```

### Current Offline Pack

El bundle vigente pasa a:

```text
IA-DOS v0.1.0-alpha.8
direct/orchestrated consistency closure
```

El Offline Pack enseña el mismo contrato que el repositorio canónico y ya no presenta a la Task física como autoridad universal.

## Superficies corregidas

La corrección C08 cubre de forma transversal:

- `README.md`;
- `AGENTS.md`;
- `ORCHESTRATOR.md`;
- `ROADMAP.md`;
- `CHANGELOG.md`;
- `docs/index.md`;
- foundations de memoria, roles, QA y working method;
- execution de coding agents y actualización de memoria;
- orchestration de gates, routing, ownership y fast planning;
- onboarding de proyectos nuevos/existentes;
- Project Orchestrator prompt;
- persistent project instructions;
- Current Offline Pack.

Las lanes y templates explícitamente ORCHESTRATED conservan Execution Task cuando esa es precisamente su frontera.

## Revalidación

Se revalidaron las superficies modificadas buscando específicamente:

- `ORCHESTRATED | DIRECT | MIXED` en contratos vigentes;
- dependencia universal de `Task vigente`;
- `Coding Agent — Execution` limitado universalmente a Execution Task;
- gates genéricos que conviertan todo outcome definido en Task;
- `Task carries authority and the active delta` como regla universal;
- alpha.7 marcado como baseline actual después de C08;
- contradicciones entre Method Resolution, Entry Policy y Entry Mode;
- regresiones en Exchange, Memory Stewardship y authority semantics.

Los matches que permanecen son deliberados cuando:

- pertenecen a evidencia histórica/CHANGELOG;
- describen una lane explícitamente ORCHESTRATED;
- explican el error corregido;
- describen Execution Resume/Checkpoint, que por definición pertenecen a una Task materializada.

## Resultado

```text
Method Resolution                    PASS
Execution Entry Mode                 PASS
Execution Entry Policy               PASS
DIRECT without physical Task         PASS
ORCHESTRATED Task contract           PASS
Generic gate semantics               PASS
Durable-memory rehydration           PASS
Coding Agent — Execution semantics   PASS
Onboarding                           PASS
Current Offline Pack                 PASS
Historical isolation                 PASS
Exchange semantics                   PASS
Memory Stewardship                   PASS
Authority model                      PASS

REPOSITORY CONSISTENCY
→ PASS AL INTEGRARSE C08
```

## Regla de continuidad

```text
resolver método
→ elegir entry mode
→ reconstruir o materializar el contrato aplicable
→ ejecutar dentro de la misma frontera material
→ dejar evidencia y continuidad proporcionales
→ reingresar gobierno sólo ante una decisión material
```

IA-DOS no debe inferir un tercer modo, no debe exigir una Task física en DIRECT y no debe rebajar los controles de autoridad por operar sin ella.

Esta auditoría es evidencia de consistencia. La fuente canónica sigue siendo el repositorio IA-DOS y el estado publicado real debe verificarse contra `main`.

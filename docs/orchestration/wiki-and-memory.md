# `90 — Documentación y memoria`

`90 — Documentación y memoria` es el Conversation Space especializado que custodia **memoria durable estructural** cuando el proyecto adopta ese rol.

Su objetivo es preservar una representación agnóstica del desarrollo: la Wiki debe explicar el proyecto vigente, sus contratos y sus fronteras, no la perspectiva accidental del último Conversation Space que implementó un cambio.

`90` no es dispatcher, no aprueba ejecución técnica y no recibe cada outcome.

## Cuándo interviene

Deriva mediante `Specialist Handoff` a `90` cuando un outcome confirmado cambia conocimiento estructural que varios agentes o dominios necesitarán reutilizar, por ejemplo:

- arquitectura o topología;
- modelo de datos o source of truth;
- seguridad, autorización, identidad o trust boundaries;
- contratos cross-domain;
- lifecycle o gobernanza;
- capacidades mayores que redefinen el estado vigente;
- reorientaciones durables;
- reorganización relevante de la propia memoria.

No uses tamaño de diff, cantidad de archivos o número de Tasks como umbral.

## Qué permanece LOCAL

No requiere `90` por defecto:

- Operational Baseline;
- release state compacto;
- bugfixes locales;
- microcopy o ajustes visuales;
- refactors internos sin cambio contractual;
- tests;
- cambios de runner o herramienta equivalente;
- memoria semántica estrecha de un dominio.

Si un cambio local revela una decisión estructural, entonces sí deriva.

## Contrato de routing

```text
Conversation Space técnico/funcional
→ completa y verifica su outcome
→ Durable Memory Impact: ROUTE_TO_90
→ Specialist Handoff inline
→ 90 — Documentación y memoria
→ revisa evidencia + memoria vigente
→ decide:
   NO UPDATE
   | CONSOLIDATE
   | MATERIALIZE NOW
→ si corresponde escritura:
   Wiki Update Task / Execution Task documental
→ Coding Agent
→ Execution Report
→ 90 revisa coherencia durable
```

`ROUTE_TO_90` significa **impacto estructural pendiente de custodia**. No implica que el outcome técnico esté incompleto.

Cuando `90` ya gobernó una Wiki Update Task y la materialización termina correctamente, ese reporte usa:

```text
Durable Memory Impact: UPDATED
```

No vuelve a emitir `ROUTE_TO_90`.

## Relación con Memory Bootstrap Gate

Un bootstrap puede ser local o estructural.

- conocimiento confirmado, estrecho y local → el Cycle Owner puede gobernar el checkpoint mínimo;
- conocimiento estructural indispensable → Specialist Handoff a `90`, que define el checkpoint durable mínimo.

El bootstrap no ejecuta la unidad original que busca desbloquear. Después de revisar el reporte documental se reevalúa el gate original.

## Relación con el Project Orchestrator

El Project Orchestrator conserva dirección del proyecto y decide el outcome que se persigue.

`90` conserva autoridad sobre **síntesis, ubicación y coherencia** de memoria estructural dentro de la autoridad delegada.

```text
Persona responsable
→ dirección y prioridad

Cycle Owner de dominio
→ outcome técnico/funcional

90
→ representación durable estructural

Coding Agent
→ materialización física autorizada
```

La custodia de `90` no transfiere roadmap ni prioridades.

## Relación con el Coding Agent

Cuando recibe una Wiki Update Task autorizada, el Coding Agent:

1. lee sólo memoria y evidencia requeridas;
2. modifica únicamente rutas autorizadas;
3. distingue hechos, decisiones, propuestas, pendientes y desconocidos;
4. preserva Markdown portable y enlaces relativos;
5. sintetiza estado resultante en vez de copiar cronología operacional;
6. mantiene `current-state` como snapshot/índice compacto;
7. revisa diff y enlaces;
8. usa Git/delivery sólo si están autorizados;
9. devuelve un Execution Report evidence-first.

El Coding Agent no decide por sí mismo qué cambio estructural merece memoria ni dónde ubicarlo antes de la custodia correspondiente.

## Operational Baseline

Operational Baseline es continuidad operacional y no activa `90` por sí solo.

Una Task BUILD/FIX/RELEASE puede actualizar dentro del mismo outcome:

- repositorio;
- branch;
- último HEAD remoto verificado;
- commit/versión publicada;
- deployment/release;
- entorno/URL;
- estado;
- fecha de verificación.

Si la publicación también cambia arquitectura, datos, seguridad, contratos cross-domain u otra dimensión estructural, actualiza el baseline localmente y deriva la síntesis semántica a `90`.

## Higiene de memoria

El camino caliente debe mantenerse pequeño:

```text
home / mapa
→ current-state compacto
→ página de dominio relevante
→ Task vigente
```

`current-state` no debe transformarse en historial acumulativo. Cuando pierde navegabilidad:

- conserva estado vigente y enlaces;
- mueve detalle reusable a páginas de dominio;
- conserva historia sólo cuando aporta continuidad;
- evita TASK/REPORT, logs, matrices, hashes y cronología exhaustiva;
- trata la reorganización como cambio estructural.

Git, plataformas de delivery y Execution Reports conservan la evidencia operacional exhaustiva.

## Límites

`90` no debe:

- convertirse en paso obligatorio posterior a cada Execution Report;
- reabrir un outcome técnico ya cerrado sólo porque existe `ROUTE_TO_90`;
- convertir hipótesis en hechos;
- registrar decisiones no confirmadas como vigentes;
- duplicar TASK/REPORT en la Wiki;
- usar la Wiki como backlog o log;
- forzar una reorganización completa cuando basta una actualización local;
- modificar recursos sin acceso y autoridad explícitos.

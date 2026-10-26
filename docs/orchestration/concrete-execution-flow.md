# Avance concreto y transición a coding agents

IA-DOS debe producir avances verificables sin depender de una plataforma, proveedor, editor o agente específico.

## Flujo principal

```text
dirección suficiente
→ outcome definido y verificable
→ asignar Cycle Owner
→ definir Protected Invariants + Protected Boundaries
→ Memory Bootstrap Gate sólo si falta memoria durable indispensable
→ Planning Task sólo si existe una decisión material no resuelta
→ Environment Preflight sólo si readiness debe conocerse antes de autorizar una frontera sensible
→ Execution Task outcome-first
   → Revalidate
   → planificar internamente
   → implementar / probar / diagnosticar / reparar / safe retry
   → cruzar fronteras autorizadas
→ Execution Report
→ revisión del Cycle Owner
→ 90 custodia memoria estructural cuando corresponda
→ persona responsable interviene ante cambio material de frontera
→ escalar a 00 sólo ante reorientación real
```

`00 — Dirección y orquestación` no es una parada obligatoria entre definición, planificación y ejecución.

## Gate de avance

Evalúa en este orden:

```text
1. ¿El outcome está suficientemente definido y verificable?
2. ¿Qué Protected Invariants deben preservarse?
3. ¿Qué Adaptation Authority puede delegarse?
4. ¿Dónde están las Protected Boundaries?
5. ¿Existe una decisión material no resuelta?
6. ¿Falta memoria durable indispensable o readiness previo a una frontera sensible?
```

- memoria estructural necesaria sólo en conversaciones → `Memory Bootstrap Gate`;
- readiness previo a autoridad sensible → `Environment Preflight`;
- decisión material no resuelta → `Planning Task`;
- outcome definido → `Execution Task` aunque falten detalles de implementación;
- decisión humana indispensable → resolver sólo esa decisión;
- reorientación → escalar a `00`.

## Memory Bootstrap operativo

Cuando el gate devuelve `BOOTSTRAP REQUIRED`:

```text
unidad original
→ queda bloqueada

Execution Task de bootstrap
→ único resultado: checkpoint durable mínimo
→ unidad original fuera de alcance
→ Execution Report
→ revisión
→ reevaluar gate original
```

La tarea de bootstrap no finge `PASS` ni ejecuta el resultado original.

## Planning Task

La Planning Task es excepcional: se usa cuando el Coding Agent no debe escribir todavía porque existe una decisión material pendiente. Los detalles de implementación y debugging ordinario se resuelven mediante planificación interna dentro de Execution.

```text
Planning Task
→ Coding Agent — Planning
→ Implementation Plan
→ revisión del Cycle Owner
→ adopción dentro de autoridad delegada
→ aprobación humana sólo cuando corresponda
→ Execution Task autorizada
```

No autoriza escritura, commits, cambios remotos, despliegues, recursos externos ni costes.

Un Implementation Plan sigue siendo propuesta, pero no exige por sí mismo una nueva aprobación humana. El Cycle Owner puede adoptarlo cuando no cambie materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

## Gate de granularidad

Antes de aprobar una Execution Task pregunta:

```text
¿Existe un outcome definido, cohesivo, acotado y verificable
que pueda completarse bajo una frontera estable de autoridad?
```

No dividas una Task sólo por duración, archivos, comandos o por contener fases internas como implementación, tests, debugging, reparación, safe retry, commit, push, deploy o smoke.

Una misma Task puede ejecutar:

```text
Revalidate
→ planificar internamente
→ Implement
→ Verify
→ Diagnose / Repair / Safe Retry
→ Commit
→ Push
→ Deploy
→ Production Smoke
→ Operational Baseline / memoria LOCAL, cuando corresponda
→ Final State
```

cuando todas las fases sirven al mismo outcome y están explícitamente autorizadas.

Divide o detén cuando cambie materialmente outcome, Protected Invariants, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste, entorno o Protected Boundary.

## Authority Envelope

Cada Execution Task puede agrupar las capacidades explícitamente autorizadas para el outcome completo.

```text
acción sensible no declarada
→ no autorizada

declarada en la Task + gates cumplidos + frontera estable
→ puede ejecutarse sin otra ida y vuelta humana por rutina

cambio material de frontera
→ STOP y nueva decisión
```

Branch, commit, push, PR, merge, deploy, producción, datos, servicios externos y costes siguen siendo capacidades separadas; ninguna se presume autorizada.

## Propiedad y responsabilidad

Todo handoff técnico declara Cycle Owner y destino del artefacto de retorno.

El Cycle Owner gobierna dentro de la autoridad delegada. La persona responsable interviene cuando una decisión cambia materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

Planes y reportes no vuelven automáticamente a `00`.

## Readiness del entorno

Toda Execution Task revalida las precondiciones volátiles indispensables al comienzo y antes de cruzar una Protected Boundary.

Usa Environment Preflight separado cuando el readiness deba conocerse antes de conceder autoridad sensible, la capacidad misma sea el resultado de la inspección o el chequeo requiera otro actor/entorno:

```text
Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

No lo uses como ritual previo a toda Execution ni dupliques checks estables que ya están cubiertos por fuentes vigentes.

## Transición visible

Cuando corresponda planificación, entrega una `Planning Task` autosuficiente al coding agent en modo de solo lectura y pide devolver el `Implementation Plan` al Cycle Owner.

Cuando corresponda preflight, entrega un `Environment Preflight` al mismo rol de solo lectura y pide devolver `Environment Readiness Report`; no lo conviertas en Planning.

Cuando corresponda ejecución, entrega una `Execution Task` completa a la Execution Cell adecuada o al entorno disponible. Reutiliza una célula activa cuando siga respondiendo bien; no abras una conversación por tarea.

Una Task es suficientemente autocontenida cuando su `Embedded Contract` más el `Required Reading` declarado permiten ejecutarla correctamente sin depender de conversaciones previas. `Reference` aporta trazabilidad y no implica lectura por defecto.

## Revisión del Implementation Plan

El Cycle Owner debe:

1. comprobar fuentes y evidencia;
2. separar hechos, inferencias y propuestas;
3. revisar dependencias, riesgos y condiciones de detención;
4. aplicar el gate de granularidad;
5. identificar cambios materiales de autoridad o riesgo;
6. adoptar dentro de autoridad delegada o derivar sólo la aprobación humana necesaria.

Plan producido no equivale a ejecución autorizada.

## Revisión del Execution Report

El destino declarado revisa:

1. outcome versus resultado;
2. alcance real versus alcance autorizado;
3. criterios versus evidencia;
4. verificaciones solicitadas versus ejecutadas;
5. autorizaciones versus acciones realizadas;
6. fuera de alcance preservado;
7. desviaciones, bloqueos y estado final;
8. Durable Memory Impact y Operational Baseline cuando la Task los declare.

El reporte es evidence-first: la Task dice qué estaba autorizado y el Report qué ocurrió realmente. No debe volver a narrar la Task.

## Tareas largas y continuidad

Una tarea larga puede materializar opcionalmente `<TASK-ID>-CHECKPOINT.md` para registrar avance, HEAD, worktree, fases completadas, pendiente y bloqueos.

El checkpoint no agrega autoridad. Un nuevo Coding Agent debe leer la Task, leer el checkpoint, verificar el estado real y continuar sólo dentro de la autoridad vigente.

`Execution Resume` conserva el mismo Task ID y equivale a `Task original + delta del bloqueo externo o interrupción real resuelta` cuando outcome, Protected Invariants, Protected Boundaries, alcance, autoridad, seguridad y arquitectura no cambiaron. No se necesita para repair-in-place o safe retry mientras la misma Execution siga abierta.

## Memoria en la misma ejecución

Toda Execution Task declara, cuando el proyecto usa memoria durable:

```text
Memory Policy: NONE | CONDITIONAL | REQUIRED
Memory Stewardship: LOCAL | 90_STRUCTURAL | NO APLICA
Operational Baseline: UPDATE_IF_PUBLISHED | UNCHANGED | NO APLICA
```

La memoria semántica no se actualiza por cada ejecución. `CONDITIONAL` sólo responde a triggers definidos por el Cycle Owner y varios outcomes menores pueden consolidarse después.

La continuidad operacional es independiente: si el outcome cambia un baseline publicado, el mismo outcome debe actualizar el checkpoint durable autorizado con repo/branch, HEAD remoto verificado, commit/versión productiva, deployment/release, entorno y fecha según aplique.

El Operational Baseline y memoria `LOCAL` pueden materializarse dentro de la misma Execution. Cuando el cambio durable es estructural y el proyecto adopta `90 — Documentación y memoria`, el executor reporta `ROUTE_TO_90` y el Cycle Owner transfiere la síntesis mediante Specialist Handoff.

Una Task WIKI separada se usa para bootstrap, consolidación, reparación, custodia estructural o una frontera de autoridad distinta; no como paso rutinario posterior.

El Coding Agent materializa memoria autorizada, pero no decide roadmap, prioridad o dirección por cuenta propia.

## Guardrails

- no enviar una intención vaga al coding agent;
- no ejecutar antes de resolver decisiones indispensables;
- no omitir Memory Bootstrap Gate cuando existe dependencia chat-only;
- no usar Environment Preflight separado cuando basta Revalidate dentro de una Task ya autorizada;
- no usar Planning para debugging o elección entre mecanismos equivalentes;
- no usar Planning para autorizar escritura implícita;
- no dividir por ceremonia una Task que conserva outcome, invariantes y frontera estables;
- no abrir una conversación por cada tarea cuando existe una Execution Cell válida;
- no regresar a `00` por rutina;
- no asumir acceso, permisos o herramientas;
- no declarar completado algo sin evidencia;
- no mezclar outcomes independientes ni cruzar una frontera material sin nueva decisión.

## Regla principal

```text
Conversar sólo lo indispensable.
Persistir memoria semántica sólo cuando haga falta.
Mantener siempre continuidad del baseline publicado cuando exista Wiki.
Revalidar readiness volátil antes de escribir o cruzar una frontera protegida.
Planificar separadamente sólo cuando exista una decisión material pendiente.
Delegar el cómo al Coding Agent dentro de Protected Invariants y Adaptation Authority.
Ejecutar el mayor outcome seguro y verificable que conserve una frontera estable de autoridad.
Derivar a 90 sólo memoria durable estructural cuando el proyecto adopte ese custodio.
Devolver evidencia al responsable declarado.
Escalar únicamente para reorientar o resolver un cambio material de frontera.
```
# Handoff entre Conversation Space y coding agent

Este flujo convierte una necesidad confirmada en inspección, planificación o ejecución acotada, verificable y trazable.

## Flujo

```text
Conversation Space
→ outcome esperado + Cycle Owner
→ Protected Invariants + Adaptation Authority + Protected Boundaries
→ Memory Bootstrap Gate sólo si falta memoria durable indispensable
→ Planning Task sólo si existe decisión material no resuelta
→ Environment Preflight sólo si readiness debe conocerse antes de autorizar una frontera sensible
→ Execution Task outcome-first + Revalidate
→ coding agent planifica internamente, ejecuta y adapta dentro de autoridad
→ retorno tipado
→ mismo Cycle Owner
→ 90 custodia memoria estructural cuando corresponda
→ revisión y decisión según autoridad
```

`00` no es una parada obligatoria.

## 1. Confirmar propiedad y destinos

Declara outcome, Cycle Owner, destino del retorno y escalamiento cuando corresponda.

El Cycle Owner actúa dentro de autoridad delegada. La persona responsable interviene cuando una decisión cambia materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

## 2. Evaluar memoria

Antes de una Planning Task o Execution Task que dependa de historia previa, aplica Memory Bootstrap Gate.

`BOOTSTRAP REQUIRED` bloquea la unidad dependiente original y permite una Execution Task separada cuyo único outcome sea materializar el checkpoint durable mínimo. Después de revisar su Report, reevalúa el gate original.

## 3. Evaluar readiness

Toda Execution Task revalida internamente las condiciones volátiles indispensables.

Prepara `Environment Preflight` en solo lectura únicamente cuando el readiness de runtime, herramienta, servicio, acceso, secreto o conectividad debe conocerse **antes de conceder autoridad sensible**, cuando la capacidad misma es el objeto de evaluación o cuando el chequeo requiere otro actor/entorno.

No crees Preflight separado si `Revalidate` dentro de una Task ya autorizada basta para actuar con seguridad.

## 4. Decidir Planning o Execution

Pregunta:

```text
¿Existe una decisión material todavía no resuelta que debe cerrarse antes de escribir?
```

- no → Execution Task; el Coding Agent planifica internamente el detalle de implementación;
- sí → Planning Task de solo lectura;
- si la decisión pertenece a otro dominio → Specialist Handoff;
- si requiere autoridad humana → deriva sólo esa decisión;
- si implica reorientación → escala a `00`.

Debugging ordinario, reparación de implementación o elección entre mecanismos técnicamente equivalentes no justifican Planning separado.

## 5. Planning Task

La Planning Task:

- es de solo lectura respecto de las fuentes, proyecto y entorno inspeccionados;
- puede materializar únicamente su propio Implementation Plan cuando Output Delivery lo autoriza;
- resuelve una decisión material dominante;
- devuelve Implementation Plan al Cycle Owner;
- no autoriza ejecución.

El plan propone, no ejecuta. El Cycle Owner puede adoptarlo dentro de autoridad delegada. No exijas automáticamente una nueva aprobación humana si el plan no cambia materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

## 6. Execution Task

La Task debe declarar:

- outcome cohesivo;
- Protected Invariants;
- Adaptation Authority: NONE | BOUNDED;
- Protected Boundaries;
- Cycle Owner y destino;
- fuentes de autoridad;
- Embedded Contract;
- Required Reading;
- References;
- alcance y fuera de alcance;
- Authority Envelope;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

No dividas la Task sólo por duración, cantidad de archivos/comandos o por contener fases de implementación, debugging, reparación, safe retry, tests, commit, push, deploy o smoke.

Puede contener:

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
→ Operational Baseline / memoria LOCAL cuando corresponda
→ Final State
```

si todas las fases sirven al mismo outcome y están autorizadas dentro de una frontera estable.

Divide o detén cuando cambie materialmente outcome, Protected Invariants, Protected Boundaries, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno.

## 7. Authority Envelope

Una acción sensible no declarada está prohibida.

Una acción explícitamente declarada en la Task, con gates previos cumplidos y frontera estable, puede ejecutarse sin otra ida y vuelta humana por rutina.

Con `Adaptation Authority: BOUNDED`, un fallo reversible sin side effects materiales se diagnostica, repara y reintenta dentro de la misma Task cuando los Protected Invariants permanecen intactos.

Branch, commit, push, PR, merge, deploy, producción, datos, servicios externos y costes siguen siendo capacidades separadas aunque puedan formar parte de la misma Task.

## 8. Ejecutar y mantener continuidad

El coding agent:

1. valida rol y Task;
2. lee Required Reading e instrucciones locales;
3. revalida el estado real;
4. planifica internamente el detalle;
5. ejecuta y adapta sólo dentro de autoridad;
6. verifica;
7. revisa el diff;
8. devuelve Execution Report.

Una Execution Cell activa se reutiliza mientras siga respondiendo bien.

Para una Task larga puede existir `<TASK-ID>-CHECKPOINT.md` con avance, HEAD/worktree, fases completadas, pendiente y bloqueos. El checkpoint no agrega autoridad.

## 9. Execution Resume

Reanuda la misma Task cuando se resolvió un bloqueo externo o una interrupción real sin cambiar outcome, Protected Invariants, Protected Boundaries, alcance, autoridad, seguridad o arquitectura.

No uses Resume para repair-in-place mientras la Execution siga abierta.

```text
Execution Resume
= Task original
+ delta del bloqueo externo o interrupción real resuelta
```

Conserva Task ID.

## 10. Execution Report

```text
Task
→ qué estaba autorizado

Report
→ qué ocurrió realmente
```

El Report debe ser evidence-first y proporcional:

- Outcome;
- Evidence;
- Actual Scope;
- Acceptance;
- Adaptations Used, sólo cuando aporte;
- Deviations;
- Final State;
- Durable Memory Impact;
- Operational Baseline.

No vuelva a narrar la Task ni seleccione la siguiente acción de gobierno.

## 11. Output Delivery y Caveman Return

Cuando la Task usa Exchange y declara `Caveman Return: Sí`, el coding agent materializa primero el output completo.

Sólo entonces la conversación puede reducirse a:

```text
EJECUCIÓN: COMPLETADO
Atención requerida: Ninguna
Reporte: <PATH>
```

No repitas tests, commits, deploy, smoke o paths que ya viven en el Report.

## 12. Exchange

Exchange es opcional, provider-agnostic, filesystem-first y pasivo.

No enruta Conversation Spaces, no es backlog, no es memoria durable y no depende de Google Drive.

Semántica mínima:

```text
inbox = artifacts operativamente activos destinados a Coding Agents
outbox = outputs pendientes de consumo o aún requeridos por trabajo activo
mantén inbox/outbox escasos; retira consumidos/superseded/duplicados sin necesidad activa
archive = cold storage operacional por trazabilidad
```

`folder ≠ workflow state` y `archive ≠ aprobado/completado/memoria durable/repositorio de documentos vivos`.

## Rechaza el cierre cuando

- falta autoridad o destino;
- un readiness que debía resolverse antes de conceder autoridad sensible sigue no listo/desconocido;
- una Task ordinaria depende de memoria chat-only no resuelta;
- cambió materialmente la frontera sin nueva decisión;
- aparecen acciones no autorizadas;
- faltan verificaciones críticas sin explicación;
- existen cambios fuera de alcance;
- el Report pretende aprobar su propio resultado o decidir memoria posterior.
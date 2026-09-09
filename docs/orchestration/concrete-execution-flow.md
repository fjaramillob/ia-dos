# Avance concreto y transición a coding agents

IA-DOS debe producir avances verificables sin depender de una plataforma, proveedor, editor o agente específico.

## Flujo principal

```text
dirección suficiente
→ siguiente resultado definido y cohesivo
→ asignar Cycle Owner
→ Memory Bootstrap Gate cuando dependa de historia conversacional
→ Environment Preflight cuando readiness indispensable sea desconocido
→ Planning Task cuando falta inspección o diseño
→ Execution Task cuando la unidad está lista
→ artefacto vuelve al Cycle Owner
→ revisión y decisión dentro de la autoridad aplicable
→ persona responsable interviene cuando corresponde
→ escalar a 00 sólo ante reorientación real
```

`00 — Dirección y orquestación` no es una parada obligatoria entre definición, planificación y ejecución.

## Gate de avance

Evalúa en este orden:

```text
1. ¿El resultado está suficientemente definido, es cohesivo, acotado y verificable bajo una frontera estable de autoridad?
2. Si depende de historia, ¿el conocimiento necesario ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿el coding agent puede proponer una unidad segura?
```

- memoria necesaria sólo en conversaciones → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección o diseño → `Planning Task`;
- todo listo → `Execution Task`;
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

La Planning Task solicita al coding agent inspeccionar fuentes y estado real en solo lectura para proponer cómo implementar.

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

No dividas una Task sólo por duración, archivos, comandos o por contener fases internas como implementación, tests, commit, push, deploy o smoke.

Una misma Task puede ejecutar:

```text
Revalidate
→ Implement
→ Verify
→ Commit
→ Push
→ Deploy
→ Production Smoke
→ Final State
```

cuando todas las fases sirven al mismo outcome y están explícitamente autorizadas.

Divide o detén cuando cambie materialmente outcome, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno.

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

Cuando una precondición indispensable no está comprobada, usa:

```text
Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

en vez de inferir que el entorno está listo.

Sólo `LISTO PARA EJECUCIÓN` permite considerar aprobación o reanudación de escritura. El readiness report no concede escritura por sí mismo.

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
7. desviaciones, bloqueos y estado final.

El reporte es evidence-first: la Task dice qué estaba autorizado y el Report qué ocurrió realmente. No debe volver a narrar la Task.

## Tareas largas y continuidad

Una tarea larga puede materializar opcionalmente `<TASK-ID>-CHECKPOINT.md` para registrar avance, HEAD, worktree, fases completadas, pendiente y bloqueos.

El checkpoint no agrega autoridad. Un nuevo Coding Agent debe leer la Task, leer el checkpoint, verificar el estado real y continuar sólo dentro de la autoridad vigente.

`Execution Resume` conserva el mismo Task ID y equivale a `Task original + delta del bloqueo resuelto` cuando objetivo, alcance, autoridad, seguridad y arquitectura no cambiaron.

## Memoria en la misma ejecución

Una actualización concreta de LLM Wiki puede formar parte de una Execution Task sólo cuando el conocimiento ya está confirmado, la modificación documental está explícitamente autorizada y no requiere una nueva decisión conceptual.

No conviertas toda ejecución de producto en una actualización automática de memoria.

## Guardrails

- no enviar una intención vaga al coding agent;
- no ejecutar antes de resolver decisiones indispensables;
- no omitir Memory Bootstrap Gate cuando existe dependencia chat-only;
- no omitir Environment Preflight cuando readiness indispensable es desconocido;
- no usar Planning para autorizar escritura implícita;
- no dividir por ceremonia una Task que conserva outcome y frontera estables;
- no abrir una conversación por cada tarea cuando existe una Execution Cell válida;
- no regresar a `00` por rutina;
- no asumir acceso, permisos o herramientas;
- no declarar completado algo sin evidencia;
- no mezclar outcomes independientes ni cruzar una frontera material sin nueva decisión.

## Regla principal

```text
Conversar sólo lo indispensable.
Persistir memoria sólo cuando haga falta.
Comprobar readiness antes de escribir.
Planificar cuando reduzca incertidumbre real.
Ejecutar el mayor outcome seguro y verificable que conserve una frontera estable de autoridad.
Devolver evidencia al responsable declarado.
Escalar únicamente para reorientar o resolver un cambio material de frontera.
```
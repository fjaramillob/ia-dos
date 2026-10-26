# Prompt de handoff hacia un coding agent

Utiliza este prompt después de autorizar una `Execution Task` con outcome definido, cohesivo, acotado y verificable bajo una frontera estable de autoridad.

Cuando la Task está materializada en Exchange, prefiere el [Manual Artifact Launcher](manual-artifact-launcher.md) para localizarla sin repetir el contrato completo.

```text
Actúa como Coding Agent — Execution para la Execution Task autorizada.

Antes de modificar:
1. lee la Execution Task canónica completa;
2. lee el Required Reading y las instrucciones locales aplicables;
3. inspecciona el estado real antes de escribir;
4. confirma outcome, Protected Invariants, Protected Boundaries, Adaptation Authority, Cycle Owner, alcance, Authority Envelope, verificaciones y stop conditions;
5. confirma Memory Policy, Memory Stewardship, Memory Triggers y regla de Operational Baseline;
6. si existe un Execution Checkpoint, léelo y verifica su estado contra la realidad; el checkpoint no agrega autoridad;
7. confirma cualquier Output Delivery declarado.

Durante la ejecución:
- trabaja únicamente dentro del outcome, Protected Invariants, Protected Boundaries y Authority Envelope;
- planifica internamente el cómo sin convertir detalles de implementación en nuevas Tasks;
- una acción sensible no declarada está prohibida;
- una acción explícitamente declarada, con gates cumplidos y frontera estable, puede ejecutarse sin pedir otra aprobación humana por rutina;
- si Adaptation Authority = BOUNDED y aparece un fallo reversible sin side effects materiales, diagnostica, repara, ajusta pruebas o mecanismo equivalente, revalida y continúa;
- no dividas ni detengas sólo porque llegaste a debugging, safe retry, tests, commit, push, deploy, smoke o actualización durable si esas fases siguen autorizadas dentro del mismo outcome;
- aplica Memory Policy sólo con los triggers definidos por el Cycle Owner;
- si Memory Stewardship = LOCAL, materializa sólo la memoria autorizada;
- si Memory Stewardship = 90_STRUCTURAL y el outcome produce impacto estructural, no sintetices la Wiki por iniciativa propia: reporta ROUTE_TO_90;
- si cambias un estado publicado y Operational Baseline = UPDATE_IF_PUBLISHED, actualiza el checkpoint durable autorizado con el estado real verificado;
- no uses la actualización de Wiki para decidir roadmap, prioridades o nuevas decisiones de producto;
- detente si cambia materialmente outcome, Protected Invariants, Protected Boundaries, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno;
- ejecuta las verificaciones aplicables;
- revisa los cambios completos.

Para continuidad larga puedes actualizar `<TASK-ID>-CHECKPOINT.md` sólo si la Task lo autoriza. Ese sidecar registra avance, HEAD/worktree, fases completadas, pendiente y bloqueos; nunca amplía autoridad.

Al finalizar, construye un Execution Report evidence-first:
- Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO;
- Atención requerida: descripción concreta o Ninguna;
- Outcome;
- Evidence;
- Actual Scope;
- Acceptance;
- Adaptations Used, sólo si aporta;
- Deviations;
- Final State;
- Durable Memory Impact: NONE | UPDATED | DEFERRED | ROUTE_TO_90 | ATTENTION REQUIRED, cuando aplica;
- Operational Baseline: UNCHANGED | UPDATED | NO APLICA | BLOQUEADO.

No vuelvas a narrar la Task ni listes permisos que no fueron utilizados sólo por ceremonia.

Si Output Delivery declara un archivo, materializa primero el Report completo en el destino autorizado.

Usa Caveman Return únicamente cuando:
1. la Task declara `Caveman Return: Sí`;
2. el Report completo fue materializado correctamente.

Entonces responde sólo:

EJECUCIÓN: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN O NINGUNA]
Reporte: [NOMBRE/PATH]

No repitas tests, paths, commits, deploy, smoke ni detalle ya contenido en el Report.

No apruebes tu propio resultado, no consolides memoria fuera de Memory Policy/Authority Envelope y no inicies otra unidad.
```

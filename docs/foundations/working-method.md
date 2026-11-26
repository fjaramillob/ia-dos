# Método de trabajo

IA-DOS separa dirección, razonamiento, materialización y verificación para permitir que personas y distintas herramientas de IA colaboren sin convertir chats, agentes o repositorios en fuentes de verdad paralelas.

## Principio rector

```text
La persona responsable dirige y conserva aprobación final aplicable.
El Project Orchestrator organiza.
Los Conversation Spaces gobiernan decisiones.
Los coding agents inspeccionan o materializan según el rol.
Las fuentes de evidencia trazan.
La memoria durable recuerda.
```

## Los cinco movimientos

```text
Entender
→ decidir
→ delimitar
→ materializar
→ verificar y aprender
```

No son fases rígidas. Se repiten tantas veces como haga falta, sin optimizar por cantidad de Tasks.

## Execution Entry Mode

Antes de decidir cómo trabajar, distingue:

```text
ORCHESTRATED
→ Conversation Space/Cycle Owner materializa gobierno antes de ejecutar

DIRECT
→ persona responsable instruye al Coding Agent directamente
→ agente reconstruye Effective Execution Contract
→ Direct Execution Gate
```

Ambos modos usan las mismas fronteras de autoridad. DIRECT elimina un handoff, no gobierno.

## 1. Entender

Lee evidencia y captura dirección suficiente antes de actuar.

Puede incluir propósito, usuario, estado real, arquitectura, decisiones vigentes, restricciones, riesgos, código, pruebas, fuentes disponibles y readiness indispensable.

El objetivo no es una auditoría exhaustiva, sino reducir supuestos que afecten la siguiente decisión.

## 2. Decidir

Confirma una decisión acotada, reversible cuando sea posible y útil para el outcome actual.

Distingue:

- hecho verificado;
- preferencia;
- supuesto;
- propuesta;
- decisión;
- pregunta abierta.

En ORCHESTRATED, el Cycle Owner actúa dentro de autoridad delegada. En DIRECT, el Coding Agent ejecuta únicamente el outcome humano vigente cuando el contrato efectivo puede reconstruirse sin ambigüedad. La persona responsable o Conversation Space interviene cuando cambian materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

Crear, materializar, rutear o iniciar una Task no es por sí mismo una decisión humana. Si dirección, outcome, invariantes, fronteras y autoridad siguen estables, el Cycle Owner continúa sin convertir la mecánica de orquestación en un checkpoint humano.

Las decisiones que deban reutilizarse se registran en memoria durable cuando corresponda.

## 3. Delimitar

Transforma la decisión en la **siguiente unidad segura**, no necesariamente en una Execution Task inmediata.

Evalúa en este orden:

```text
1. ¿El outcome está definido y es verificable?
2. ¿Cuáles son los Protected Invariants?
3. ¿Qué Adaptation Authority puede delegarse?
4. ¿Dónde están las Protected Boundaries?
5. ¿Existe una decisión material todavía no resuelta?
6. ¿Falta memoria durable indispensable o readiness que deba conocerse antes de autoridad sensible?
```

Resultados:

- historia durable indispensable ausente → `Memory Bootstrap Gate`;
- decisión material no resuelta → `Planning Task`;
- readiness que debe conocerse antes de conceder autoridad sensible, capacidad que es objeto de evaluación o chequeo que requiere otro actor/entorno → `Environment Preflight`;
- outcome definido → `ORCHESTRATED`: `Execution Task` con Revalidate y planificación interna; `DIRECT`: `Effective Execution Contract` + Direct Execution Gate, sin Task física obligatoria.

En ORCHESTRATED, una Execution Task declara proporcionalmente los campos siguientes. En DIRECT, el Effective Execution Contract debe permitir reconstruir los equivalentes que apliquen sin fabricar una Task física:

- outcome;
- Cycle Owner y destino;
- Execution Cell o sesión cuando corresponda;
- Embedded Contract;
- Required Reading y References cuando aporten;
- alcance y fuera de alcance;
- Protected Invariants;
- Adaptation Authority;
- Protected Boundaries;
- Authority Envelope;
- Memory Policy, Memory Stewardship y regla de Operational Baseline cuando aplica;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

No dividas una Task sólo por duración, cantidad de archivos/comandos o porque internamente incluya implementación, debugging, repair, safe retry, tests, commit, push, deploy o smoke. Divide o detén cuando cambie materialmente outcome, Protected Invariants, Protected Boundaries, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno.

## 3.5 Direct Execution Gate

En DIRECT, antes de escribir confirma:

- outcome suficientemente claro;
- Protected Invariants reconstruibles;
- Protected Boundaries identificables;
- autoridad necesaria disponible;
- aceptación verificable;
- memoria durable suficiente para no depender de conversaciones ausentes.

Si falla por una decisión de gobierno, devuelve `NEEDS_GOVERNANCE`. Si la duda es técnica y está dentro de `BOUNDED`, self-plan y continúa.

## 4. Materializar

La modificación física se delega a `Coding Agent — Execution` con acceso adecuado y una Execution Task autorizada.

El coding agent revalida, planifica internamente, modifica, prueba y reporta dentro de la Execution Task o, en DIRECT, dentro del Effective Execution Contract derivado de la instrucción humana y fuentes durables.

Con `Adaptation Authority: BOUNDED`, un fallo técnico reversible se diagnostica, repara y reintenta dentro de la misma Execution cuando no hubo side effects materiales y permanecen estables outcome, Protected Invariants y Protected Boundaries.

Una misma Task puede contener fases internas de revalidación, implementación, debugging, reparación, safe retry, verificación, Git, delivery, smoke y memoria `LOCAL` cuando corresponde, si sirven al mismo outcome y están explícitamente autorizadas bajo una frontera estable.

Una Execution Cell puede preservar continuidad entre tareas, pero no hereda permisos.

`Execution Resume` se usa sólo después de una interrupción real, acción externa, Human Decision Checkpoint resuelto o bloqueo que el executor no podía resolver dentro de su autoridad. Sólo aplica si outcome, Protected Invariants, Protected Boundaries, alcance, autoridad, seguridad y arquitectura siguen sin cambios. Su semántica es `Task original + delta del bloqueo externo, interrupción real o Human Decision Checkpoint resuelto`. Repair-in-place durante una Execution abierta no exige Resume.

Para una tarea larga puede existir un sidecar operacional `<TASK-ID>-CHECKPOINT.md`. Registra continuidad, no autorización.

Una Task larga puede declarar Human Decision Checkpoints. El executor avanza hasta el checkpoint, se detiene antes de la acción protegida y deriva sólo la decisión material. Si la respuesta humana activa una opción ya prevista y no cambia la frontera, la misma Task continúa con `Execution Resume` y el mismo Task ID.

## 5. Verificar y aprender

Revisa el resultado contra la tarea, no contra la confianza que inspire el agente.

La verificación puede incluir diff, lint, typecheck, build, pruebas, revisión visual, seguridad, logs, deployment checks o pasos manuales reproducibles.

El Execution Report utiliza:

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

Es evidence-first y proporcional:

```text
Task
→ qué estaba autorizado

Report
→ qué ocurrió realmente
```

No debe volver a narrar la Task. Prioriza `Outcome`, `Evidence`, `Actual Scope`, `Acceptance`, `Deviations` y `Final State`.

Después de revisar:

- la implementación queda en su fuente técnica;
- la evidencia queda en Report, diff, PR u otro mecanismo;
- el trabajo pendiente queda en el sistema de seguimiento;
- la memoria semántica se actualiza según `Memory Policy` y `Memory Stewardship`;
- impacto `90_STRUCTURAL` pendiente de custodia se reporta `ROUTE_TO_90` sin reabrir el outcome técnico;
- si cambió un baseline publicado, el checkpoint operacional durable debe reflejar el estado final verificado;
- varios outcomes menores pueden consolidarse más adelante en una sola actualización semántica cuando juntos cambien la comprensión vigente;
- `DEFERRED` deja de ser suficiente cuando la acumulación cambia estado actual, outcome activo, milestone/capability, blocker material, horizonte aceptado o autoridad vigente;
- la superficie caliente de memoria debe permitir responder qué está vigente ahora sin recorrer historia exhaustiva.

No copies conversaciones completas ni conviertas cada hallazgo en memoria permanente. Tampoco uses esta selectividad para dejar a un futuro agente sin saber qué versión está publicada.

## Arquitectura operativa

```text
Persona responsable
        ↓
Project Orchestrator
        ↓
Conversation Space / Cycle Owner
        ↓
resultado definido y cohesivo
        ↓
Memory Bootstrap Gate, cuando falta memoria durable indispensable
        ↓
Planning Task, sólo si existe decisión material no resuelta
        ↓
Environment Preflight, sólo si readiness debe conocerse antes de autoridad sensible
        ↓
Execution Task outcome-first + Revalidate
        ↓
Execution Cell o entorno autorizado
        ↓
Coding Agent
        ↓
Execution Report
        ↓
Cycle Owner revisa
        ↓
Persona responsable interviene cuando corresponde
        ↓
Fuentes de verdad actualizadas cuando aplica
```

## Regla de frontera

```text
Project Orchestrator / Cycle Owner
    define y delimita dentro de autoridad delegada

Coding Agent — Planning
    inspecciona y propone

Coding Agent — Execution
    realiza el cambio físico y entrega evidencia
```

El Orchestrator no presenta una propuesta como implementada. El coding agent no convierte una instrucción acotada en una decisión de producto, arquitectura o gobierno.

Una acción sensible no declarada en el Authority Envelope no está autorizada. Una acción declarada, con gates previos cumplidos y dentro de la misma frontera, no requiere otra ida y vuelta humana por rutina.

## Trabajo progresivo

IA-DOS favorece outcomes seguros y verificables que funcionan y evolucionan.

No exige completar toda la definición, documentación o arquitectura antes de construir. Exige claridad suficiente y una frontera estable para el siguiente avance seguro.

La memoria durable aparece cuando hace falta para preservar conocimiento reusable, no como ceremonia previa a cada avance. Una LLM Wiki es una posible materialización de esa memoria, no una topología obligatoria.

Cuando existe, debe superar una prueba práctica: un Coding Agent nuevo puede ponerse al día con `repositorio + Wiki relevante + contrato de ejecución aplicable`, reconocer el último baseline publicado y revalidar la realidad antes de aportar.
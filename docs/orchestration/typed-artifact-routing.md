# Tipado de artefactos y validación del receptor

Este contrato evita que un bloque destinado a un Conversation Space sea interpretado como una tarea para un coding agent, o viceversa.

## Encabezado fuerte

Todo bloque transferible nuevo comienza con:

```text
Artifact Type: [TIPO]
Destination Role: [ROL RECEPTOR]
Expected Output: [ARTEFACTO O REVISIÓN]
Forbidden Output: [ARTEFACTO O ACCIÓN]
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID O NO APLICA]
```

El receptor valida el encabezado antes de actuar.

## Tipos canónicos

- Specialist Handoff;
- Planning Task;
- Environment Preflight;
- Environment Readiness Report;
- Implementation Plan;
- Execution Task;
- Execution Resume;
- Execution Report.

El transporte, almacenamiento o una convención operacional no crea tipos adicionales.

```text
Authority Envelope ≠ Artifact Type
Execution Checkpoint ≠ Artifact Type
Manual Artifact Launcher ≠ Artifact Type
Output Delivery ≠ Artifact Type
Caveman Return ≠ Artifact Type
Exchange ≠ Artifact Type
```

`Wiki Update Task` continúa siendo un perfil documental de Execution Task, no un tipo independiente.

## Frontera de transporte

```text
Conversation Space → Conversation Space
→ Specialist Handoff inline, autocontenido y copiable
→ no requiere `.md`, Exchange, path ni Manual Artifact Launcher

Conversation Space → Coding Agent
→ Planning Task | Environment Preflight | Execution Task | Execution Resume
→ chat o `.md`/Exchange según el contrato de entrega
```

Exchange no enruta Conversation Spaces.

## Identidad

El Conversation Agent que construye una Execution Task asigna el `Task ID` antes del handoff o materialización.

Una candidata de Planning declara:

```text
Task ID: PENDIENTE — ASIGNAR AL ADOPTAR
```

El Execution Report reutiliza exactamente el Task ID de su Task.

`Cycle ID` puede ser `NO APLICA`.

## Specialist Handoff

```text
Artifact Type: Specialist Handoff
Destination Role: Conversation Space — [TÓPICO]
Expected Output: decisión de dominio | Planning Task | Environment Preflight | Execution Task
Forbidden Output: Implementation Plan | Execution Report | cambios técnicos
```

Es inline y copiable. Si el proyecto usa Exchange, el handoff puede declarar esa adopción para artifacts hacia/desde Coding Agents, nunca como routing conversacional.

Un Conversation Space nuevo, retomado tras un cambio relevante de IA-DOS o que muestre reglas obsoletas puede realizar IA-DOS Alignment condicional antes de decidir, sin reiniciar onboarding ni releer todo el framework.

## Planning Task

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios del proyecto | ejecución
```

El plan propone y no se autoaprueba. El Cycle Owner puede adoptarlo dentro de autoridad delegada; la persona responsable interviene cuando cambia materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

## Environment Preflight

```text
Artifact Type: Environment Preflight
Destination Role: Coding Agent — Planning
Expected Output: Environment Readiness Report
Forbidden Output: cambios del entorno | ejecución
```

Estados de salida: `LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO`.

## Execution Task

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar outcome o frontera | aprobar el propio resultado | iniciar otra unidad
```

Debe perseguir un outcome definido, cohesivo, acotado y verificable bajo una frontera estable de autoridad.

Puede incluir fases internas de implementación, pruebas, Git, delivery o smoke sin crear Tasks separadas cuando todas sirven al mismo outcome.

### Authority Envelope

Vive dentro de Execution Task y declara capacidades sensibles explícitas.

```text
acción sensible no declarada → no autorizada
acción declarada + gates cumplidos + frontera estable → puede ejecutarse dentro de la misma Task
cambio material de frontera → STOP
```

No es un Artifact Type.

### Contexto

La Task distingue:

```text
Embedded Contract
→ autoridad y límites que deben viajar

Required Reading
→ documentos que sí deben consumirse

Reference
→ trazabilidad/navegación; no implica lectura
```

`Task + Required Reading` deben permitir ejecutar sin depender de conversaciones previas.

### Execution Checkpoint

`<TASK-ID>-CHECKPOINT.md` puede registrar continuidad operacional de una Task larga o un cambio de Coding Agent.

No es Artifact Type ni autorización.

## Execution Resume

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: replantear arquitectura | ampliar outcome | ampliar permisos
```

Semántica:

```text
Execution Resume = Task original + delta del bloqueo resuelto
```

Conserva Task ID y sólo aplica si objetivo, alcance, autoridad, seguridad y arquitectura siguen sin cambios.

## Execution Report

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión de evidencia bajo la autoridad aplicable
Forbidden Output: aprobar el propio resultado | iniciar automáticamente otra unidad
```

`Task = qué estaba autorizado`; `Report = qué ocurrió realmente`.

Estructura preferente: `Outcome`, `Evidence`, `Actual Scope`, `Acceptance`, `Deviations`, `Final State`.

No vuelva a narrar la Task.

## Output Delivery, Launcher y Caveman Return

Cuando una Task autoriza:

```text
Output Delivery:
Channel: Exchange
Location: outbox
Filename: <TASK-ID>-REPORT.md
Caveman Return: Sí
```

el output completo se materializa primero. Sólo entonces la conversación puede devolver estado, atención requerida y path.

El Manual Artifact Launcher únicamente localiza la Task y, cuando hace falta, el path físico de output. Nunca modifica autoridad.

## Gate de compatibilidad

Antes de actuar valida:

1. ¿Mi rol coincide con `Destination Role`?
2. ¿La salida coincide con `Expected Output`?
3. ¿La acción está explícitamente autorizada?
4. ¿Existe contradicción entre encabezado y cuerpo?
5. ¿El transporte corresponde al receptor?
6. ¿La acción permanece dentro de la frontera material de la Task?

Ante contradicción prevalece la opción más restrictiva.
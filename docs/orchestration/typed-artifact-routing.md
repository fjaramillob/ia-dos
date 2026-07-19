# Tipado de artefactos y validación del receptor

Este contrato evita que un bloque destinado a un Conversation Space sea interpretado como una tarea para un coding agent, o viceversa.

## Regla principal

Todo bloque transferible nuevo debe comenzar con:

```text
Artifact Type: [TIPO]
Destination Role: [ROL RECEPTOR]
Expected Output: [ARTEFACTO]
Forbidden Output: [ARTEFACTO O ACCIÓN]
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID O NO APLICA]
```

El receptor valida el encabezado antes de actuar.

## Compatibilidad de transición

`Artifact: Implementation Plan` y `Artifact: Execution Report` siguen siendo alias heredados cuando el cuerpo conserva IDs, sesión, Cycle Owner, estado y decisión requerida. Las salidas nuevas usan `Artifact Type:`.

## Tipos permitidos

### Specialist Handoff

```text
Artifact Type: Specialist Handoff
Destination Role: Conversation Space — [TÓPICO]
Expected Output: decisión de dominio | Planning Task | Execution Task
Forbidden Output: Implementation Plan | Execution Report | cambios técnicos
```

### Planning Task

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios | commits | despliegues | Execution Report
```

### Environment Preflight

```text
Artifact Type: Environment Preflight
Destination Role: Coding Agent — Planning
Expected Output: Environment Readiness Report
Forbidden Output: cambios | instalaciones | inicio de servicios | ejecución
```

El preflight conserva el ciclo vigente y solo comprueba precondiciones.

### Implementation Plan

```text
Artifact Type: Implementation Plan
Destination Role: Cycle Owner — Conversation Space
Expected Output: Aprobar | Corregir | Rechazar | Escalar
Forbidden Output: ejecución automática
```

### Execution Task

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar alcance | aprobar el propio resultado | iniciar otra unidad
```

### Execution Resume

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: nueva Planning Task | replantear arquitectura | ampliar alcance
```

Conserva Cycle ID y Task ID. Reanuda una tarea aprobada después de resolver una condición bloqueante.

### Execution Report

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: Cerrar | Corregir | Revertir | Escalar
Forbidden Output: iniciar automáticamente el siguiente ciclo
```

## Gate de compatibilidad

Antes de responder, valida:

1. ¿Mi rol coincide con `Destination Role`?
2. ¿El artefacto solicitado coincide con `Expected Output`?
3. ¿La acción requerida está autorizada?
4. ¿Existe una contradicción entre encabezado y cuerpo?

Cuando el rol no coincida, no ejecutes: indica el rol esperado y devuelve el bloque sin transformarlo silenciosamente. Ante contradicción prevalece la opción más restrictiva.

## Reglas por receptor

Un Conversation Space puede recibir Specialist Handoff, Environment Readiness Report, Implementation Plan o Execution Report.

Un coding agent puede recibir Planning Task, Environment Preflight, Execution Task o Execution Resume.

Ningún coding agent asume identidad de Conversation Space, Cycle Owner o Project Orchestrator ni decide el siguiente ciclo.

## Cierre

El encabezado funciona como un tipo fuerte: declara quién puede actuar, qué puede producir y qué está prohibido.

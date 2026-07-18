# Tipado de artefactos y validación del receptor

Este contrato evita que un bloque destinado a un Conversation Space sea interpretado como una tarea para un coding agent, o viceversa.

## Regla principal

Todo bloque transferible debe comenzar con un encabezado de transporte:

```text
Artifact Type: [TIPO]
Destination Role: [ROL RECEPTOR]
Expected Output: [ARTEFACTO]
Forbidden Output: [ARTEFACTO O ACCIÓN]
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID O NO APLICA]
```

El receptor debe validar el encabezado antes de actuar.

## Tipos permitidos

### Specialist Handoff

```text
Artifact Type: Specialist Handoff
Destination Role: Conversation Space — [TÓPICO]
Expected Output: decisión de dominio | Planning Task | Execution Task
Forbidden Output: Implementation Plan | Execution Report | cambios técnicos
```

Un Specialist Handoff transfiere gobierno o una decisión. No autoriza al Conversation Space a actuar como coding agent.

### Planning Task

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios, commits, despliegues, Execution Report
```

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
4. ¿Existe una contradicción entre el encabezado y el cuerpo?

Cuando el rol no coincida:

- no ejecutes el artefacto;
- indica el rol esperado;
- devuelve el bloque al usuario sin transformarlo silenciosamente.

Cuando el encabezado y el cuerpo discrepen, prevalece la opción más restrictiva y se solicita corrección al emisor.

## Regla para Conversation Spaces

Un Conversation Space puede recibir un Specialist Handoff, Implementation Plan o Execution Report.

No debe recibir una Planning Task o Execution Task como si fuera el coding agent, salvo que se cumpla la excepción explícita de doble rol definida por IA-DOS.

## Regla para coding agents

Un coding agent puede recibir una Planning Task o Execution Task.

No debe asumir identidad de Conversation Space, Cycle Owner o Project Orchestrator, ni decidir el siguiente ciclo.

## Cierre

El encabezado de transporte funciona como un tipo fuerte: declara quién puede actuar, qué puede producir y qué está prohibido. Ningún receptor debe inferir o cambiar silenciosamente el tipo del artefacto.
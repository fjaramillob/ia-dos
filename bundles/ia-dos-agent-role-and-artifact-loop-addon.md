# IA-DOS Agent Role and Artifact Loop Addendum

Complemento obligatorio del pack operativo para plataformas sin acceso al repositorio canónico.

Usa este archivo junto con:

- `ia-dos-project-orchestrator-pack.md`;
- `ia-dos-fast-planning-addon.md`.

## Flujo

```text
Conversation Space especialista
→ tarea autosuficiente
→ sesión acotada del coding agent
→ Implementation Plan o Execution Report
→ revisión del Cycle Owner
→ siguiente decisión
```

## Contrato de rol obligatorio

Toda Planning Task y Execution Task dirigida a un coding agent debe incluir:

```text
Método: IA-DOS
Rol activo: Coding Agent — Planning | Coding Agent — Execution
Cycle ID: [CYCLE-ID]
Task ID: [TASK-ID]
Agent Session: [NOMBRE]
Cycle Owner: [CONVERSATION SPACE]
Artefacto de entrada: Planning Task | Execution Task
Artefacto de salida: Implementation Plan | Execution Report
Destino: [CONVERSATION SPACE]
Autoridad: [SOLO LECTURA | ESCRITURA ACOTADA]
```

El coding agent no actúa como `00`, no cambia ownership, no aprueba su propio resultado, no amplía alcance y no inicia otra unidad ni otro ciclo.

## Sesiones separadas

Para planificación:

```text
PLAN — [RESULTADO]
```

Para ejecución:

```text
[RESULTADO]
```

Ejemplo:

```text
PLAN — BOOTSTRAP
BOOTSTRAP
```

No reutilices la sesión de planificación para ejecutar. Cuando la herramienta no permita nombrar sesiones, abre una sesión independiente y conserva el nombre lógico dentro de la tarea y del artefacto.

## Identificadores trazables

```text
Cycle ID: CYCLE-[RESULTADO]-[N]
Planning Task: PLAN-[RESULTADO]-[N]
Implementation Plan: IP-[RESULTADO]-[N]
Execution Task: EXEC-[RESULTADO]-[N]
Execution Report: ER-[RESULTADO]-[N]
```

## Encabezado del Implementation Plan

```text
Artifact: Implementation Plan
Cycle ID: [CYCLE-ID]
Planning Task ID: [PLAN-ID]
Agent Session: PLAN — [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
Decisión requerida: Aprobar | Corregir | Rechazar | Escalar
```

## Encabezado del Execution Report

```text
Artifact: Execution Report
Cycle ID: [CYCLE-ID]
Execution Task ID: [TASK-ID]
Agent Session: [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Decisión requerida: Aprobar | Corregir | Revertir | Escalar
```

## Acceso a IA-DOS

Declara uno de estos modos:

- `Embedded Contract`;
- `Remote Repository`;
- `Local Reference`.

Una referencia local compartida permitida puede ubicarse fuera del producto:

```text
Proyectos/
├── 00-ia-dos/
└── [Proyecto]/
    ├── [proyecto-app]/
    └── [proyecto-wiki]/
```

La topología es opcional. No clones IA-DOS dentro de la aplicación o la Wiki del producto. No realices clones silenciosos; solicita autorización antes de crear una referencia local.

## Revisión

El coding agent produce artefactos. El Conversation Space especialista revisa y toma la siguiente decisión.

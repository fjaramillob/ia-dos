# Roles, sesiones y ciclo de artefactos

Este contrato define el intercambio repetible entre Conversation Spaces especialistas y coding agents.

## Flujo canónico

```text
Conversation Space especialista
→ tarea autosuficiente
→ sesión acotada del coding agent
→ artefacto verificable
→ revisión del Cycle Owner
→ siguiente decisión
```

El especialista gobierna el resultado. El coding agent planifica o ejecuta únicamente la tarea recibida y devuelve el artefacto solicitado.

## Roles protegidos

### Cycle Owner — Conversation Space especialista

Puede definir el resultado, preparar tareas, revisar artefactos, aprobar o corregir y determinar la siguiente unidad.

No debe ejecutar su propia Planning Task salvo la excepción explícita ya definida por IA-DOS.

### Coding Agent — Planning

Puede inspeccionar, verificar, comparar, proponer y preparar una Execution Task candidata.

No puede escribir, aprobar su propio plan, ejecutar, cambiar el Cycle Owner, actuar como `00` ni abrir un nuevo ciclo.

### Coding Agent — Execution

Puede modificar únicamente lo autorizado, ejecutar verificaciones y producir evidencia.

No puede ampliar alcance, iniciar otra unidad, aprobar su propio resultado, integrar o desplegar sin autorización explícita.

## Contrato de rol IA-DOS

Toda Planning Task y Execution Task dirigida a un coding agent debe declarar:

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

También debe recordar que el coding agent no aprueba su resultado, no redefine ownership y no actúa como Project Orchestrator.

## Sesiones del coding agent

Usa una sesión independiente por resultado y por nivel de autorización.

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

Cuando la herramienta permita nombrar conversaciones o sesiones, crea el nombre indicado. Cuando no lo permita, abre una sesión independiente y declara el nombre lógico dentro del artefacto.

No reutilices la sesión de planificación para ejecutar. El cambio de sesión hace visible el cambio desde solo lectura hacia escritura autorizada.

## Identificadores estables

Cada ciclo debe mantener una cadena trazable:

```text
Cycle ID: CYCLE-[RESULTADO]-[N]
Planning Task: PLAN-[RESULTADO]-[N]
Implementation Plan: IP-[RESULTADO]-[N]
Execution Task: EXEC-[RESULTADO]-[N]
Execution Report: ER-[RESULTADO]-[N]
```

Los identificadores no necesitan un sistema central. Deben ser consistentes dentro del ciclo y evitar mezclar versiones.

## Acceso a IA-DOS

Declara uno de estos modos:

- `Embedded Contract`: el contrato de rol está contenido en la tarea;
- `Remote Repository`: el agente puede consultar la fuente canónica remota;
- `Local Reference`: existe una referencia local compartida.

La tarea debe ser autosuficiente incluso cuando la referencia canónica no sea accesible.

### Referencia local compartida

Una organización local válida puede ser:

```text
Proyectos/
├── 00-ia-dos/
└── [Proyecto]/
    ├── [proyecto-app]/
    └── [proyecto-wiki]/
```

Esta topología es una configuración permitida, no un requisito universal.

`00-ia-dos` es una referencia compartida fuera del repositorio del producto. No copies ni clones IA-DOS dentro de la aplicación o la Wiki del proyecto.

Si la referencia local no existe:

1. usa el contrato embebido;
2. usa la fuente remota cuando esté disponible;
3. solicita autorización antes de clonar o crear una referencia local;
4. no realices un clon silencioso.

## Contrato de retorno

Todo artefacto debe comenzar con un encabezado estable.

### Implementation Plan

```text
Artifact: Implementation Plan
Planning Task ID: [PLAN-ID]
Agent Session: PLAN — [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
Decisión requerida: Aprobar | Corregir | Rechazar | Escalar
```

### Execution Report

```text
Artifact: Execution Report
Execution Task ID: [TASK-ID]
Agent Session: [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Decisión requerida: Aprobar | Corregir | Revertir | Escalar
```

## Gate de revisión

Al recibir un Implementation Plan, el Cycle Owner no reinicia el diagnóstico. Comprueba evidencia, tamaño y seguridad, y aprueba o corrige una sola Execution Task candidata.

Al recibir un Execution Report, comprueba objetivo, alcance, criterios y evidencia. Luego cierra, emite una corrección acotada, revierte, inicia un ciclo nuevo o escala solo ante reorientación real.

## Regla principal

Cada intercambio debe conservar rol, autorización, identificadores, sesión y destino. El coding agent produce artefactos; el Conversation Space especialista toma decisiones.
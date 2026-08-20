# Roles, sesiones y ciclo de artefactos

Este contrato define el intercambio repetible entre Conversation Spaces especialistas y coding agents.

## Flujo canónico

```text
Conversation Space especialista
→ tarea autosuficiente
→ Execution Cell activa del coding agent
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

Toda Planning Task y Execution Task dirigida a un coding agent debe declarar el rol y la autoridad aplicables.

Cuando se use el contrato clásico por ciclo puede incluir:

```text
Método: IA-DOS
Rol activo: Coding Agent — Planning | Coding Agent — Execution
Cycle ID: [CYCLE-ID]
Task ID: [TASK-ID]
Agent Session o Execution Cell: [NOMBRE]
Cycle Owner: [CONVERSATION SPACE]
Artefacto de entrada: Planning Task | Execution Task
Artefacto de salida: Implementation Plan | Execution Report
Destino: [CONVERSATION SPACE]
Autoridad: [SOLO LECTURA | ESCRITURA ACOTADA]
```

También debe recordar que el coding agent no aprueba su resultado, no redefine ownership y no actúa como Project Orchestrator.

## Sesiones de planificación

La planificación conserva una frontera visible de autorización.

Para planificación puede utilizarse:

```text
PLAN — [RESULTADO]
```

La sesión de planificación es de solo lectura y no se convierte automáticamente en ejecución.

## Execution Cells

Las tareas de ejecución no requieren una conversación nueva por resultado.

Una `Execution Cell` es un contexto durable de ejecución definido por proyecto. Cuando la herramienta ofrece conversaciones persistentes, mantén una sola conversación activa por célula mientras siga respondiendo bien.

Ejemplos:

```text
App
Wiki Sync
```

No crees células únicamente porque existan especialidades diferentes como frontend, backend, QA o DevOps. Una célula nueva se justifica cuando mantener ese contexto separado produce una ventaja operacional real.

La conversación puede renovarse cuando exista evidencia de degradación o contaminación de contexto:

```text
App · 01 → cerrada
App · 02 → activa
```

La renovación no cambia la identidad de la célula ni obliga a reiniciar el proyecto.

Consulta [Execution Cells y Exchange Protocol v0](../execution/execution-cells-and-exchange.md).

## Autorización no acumulativa

Reutilizar una conversación no reutiliza automáticamente los permisos de tareas anteriores.

Cada `Execution Task` vuelve a delimitar:

- objetivo;
- alcance;
- restricciones;
- capacidades autorizadas;
- acciones externas;
- criterios de aceptación;
- condiciones de detención.

El coding agent no inicia la siguiente unidad por sí mismo.

## Identificadores estables

IA-DOS admite dos esquemas según el modo operativo.

### Ciclo clásico

```text
Cycle ID: CYCLE-[RESULTADO]-[N]
Planning Task: PLAN-[RESULTADO]-[N]
Implementation Plan: IP-[RESULTADO]-[N]
Execution Task: EXEC-[RESULTADO]-[N]
Execution Report: ER-[RESULTADO]-[N]
```

### Exchange Protocol v0

Cuando varias Conversation Spaces emiten tareas hacia Execution Cells persistentes sin un registro central compartido:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

El `REPORT` reutiliza exactamente el mismo ID del `TASK`.

Ejemplo:

```text
PROPACTO-10-APP-20260819-230215-TASK.md
PROPACTO-10-APP-20260819-230215-REPORT.md
```

Los esquemas no deben mezclarse dentro de un mismo intercambio.

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
    ├── [proyecto-wiki]/
    └── [proyecto-exch]/
```

Esta topología es una configuración permitida, no un requisito universal.

`00-ia-dos` es una referencia compartida fuera del repositorio del producto. No copies ni clones IA-DOS dentro de la aplicación o la Wiki del proyecto.

Si la referencia local no existe:

1. usa el contrato embebido;
2. usa la fuente remota cuando esté disponible;
3. solicita autorización antes de clonar o crear una referencia local;
4. no realices un clon silencioso.

## Contrato de retorno

Todo artefacto debe comenzar con un encabezado estable suficiente para vincularlo con su tarea.

### Implementation Plan

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

### Execution Report

En el flujo clásico:

```text
Artifact: Execution Report
Cycle ID: [CYCLE-ID]
Execution Task ID: [TASK-ID]
Execution Cell o Agent Session: [NOMBRE]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Decisión requerida: Aprobar | Corregir | Revertir | Escalar
```

En Exchange v0 puede usarse la plantilla compacta `templates/exchange-report-v0.template.md`.

## Gate de revisión

Al recibir un Implementation Plan, el Cycle Owner no reinicia el diagnóstico. Comprueba evidencia, tamaño y seguridad, y aprueba o corrige una sola Execution Task candidata.

Al recibir un Execution Report, comprueba objetivo, alcance, criterios y evidencia. Luego cierra, emite una corrección acotada, revierte, inicia una nueva unidad o escala solo ante reorientación real.

## Regla principal

Cada intercambio debe conservar rol, autorización, identificadores y destino. Las conversaciones de ejecución pueden persistir; la autoridad de cada tarea no. El coding agent produce artefactos y el Conversation Space especialista toma decisiones.

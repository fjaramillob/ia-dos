# Roles, sesiones y ciclo de artefactos

Este contrato define el intercambio repetible entre Conversation Spaces especialistas y coding agents.

## Flujo canónico

```text
Conversation Space especialista
→ tarea autosuficiente
→ coding agent planifica o ejecuta según el rol asignado
→ artefacto verificable
→ revisión del Cycle Owner
→ siguiente decisión
```

Cuando el proyecto utiliza Execution Cells, la ejecución puede ocurrir dentro de una conversación persistente asociada a la célula.

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

Un contrato puede incluir:

```text
Método: IA-DOS
Rol activo: Coding Agent — Planning | Coding Agent — Execution
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID]
Agent Session o Execution Cell: [NOMBRE CUANDO CORRESPONDA]
Cycle Owner: [CONVERSATION SPACE]
Artefacto de entrada: Planning Task | Execution Task
Artefacto de salida: Implementation Plan | Execution Report
Destino: [CONVERSATION SPACE]
Autoridad: [SOLO LECTURA | ESCRITURA ACOTADA]
```

El coding agent no aprueba su resultado, no redefine ownership y no actúa como Project Orchestrator.

## Sesiones de planificación

La planificación conserva una frontera visible de autorización y es siempre de solo lectura.

Puede utilizarse un identificador lógico como:

```text
PLAN — [RESULTADO]
```

IA-DOS no establece todavía una política universal sobre si las conversaciones de planificación deben persistir, reutilizarse o renovarse. No abras una conversación nueva por tarea únicamente porque el ejemplo use un nombre `PLAN — ...`.

La planificación nunca se convierte automáticamente en ejecución.

## Execution Cells

Las tareas de ejecución no requieren una conversación nueva por resultado.

Una `Execution Cell` es un contexto durable de ejecución definido por proyecto. Cuando la herramienta ofrece conversaciones persistentes, mantén una sola conversación activa por célula mientras siga respondiendo bien.

Ejemplos genéricos:

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
- alcance y fuera de alcance;
- autoridad y acceso;
- restricciones;
- capacidades autorizadas;
- acciones externas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

El coding agent no inicia la siguiente unidad por sí mismo.

## Contrato semántico y transporte

IA-DOS distingue el artefacto de su mecanismo de transporte.

```text
Execution Task
    define la unidad y sus límites

Exchange Protocol v0
    identifica, conserva y transporta TASK/REPORT
```

Una tarea enviada mediante Exchange sigue siendo `Artifact Type: Execution Task` y dirigida a `Coding Agent — Execution`.

Una Execution Cell identifica continuidad de ejecución; tampoco sustituye el rol receptor.

## Identificadores estables

IA-DOS admite distintos esquemas de identificación según el modo operativo, sin cambiar el tipo del artefacto.

### Ciclo clásico

```text
Cycle ID: CYCLE-[RESULTADO]-[N]
Planning Task: PLAN-[RESULTADO]-[N]
Implementation Plan: IP-[RESULTADO]-[N]
Execution Task: EXEC-[RESULTADO]-[N]
Execution Report: ER-[RESULTADO]-[N]
```

### Exchange Protocol v0

Cuando no existe un registro central compartido, puede usarse como `Task ID`:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

El `REPORT` reutiliza exactamente el mismo `Task ID` del `TASK`.

Ejemplo genérico:

```text
PORTAL-10-APP-20260819-230215-TASK.md
PORTAL-10-APP-20260819-230215-REPORT.md
```

Cuando Exchange no participa de un ciclo separado:

```text
Cycle ID: NO APLICA
```

No mezcles dos identificadores de tarea para el mismo intercambio.

## Acceso a IA-DOS

Declara uno de estos modos cuando aporte:

- `Embedded Contract`: el contrato necesario está contenido en la tarea;
- `Remote Repository`: el agente puede consultar la fuente canónica remota;
- `Local Reference`: existe una referencia local compartida.

La tarea debe conservar suficientes controles para ejecutarse con seguridad incluso cuando la referencia canónica no sea accesible.

### Referencia local compartida

Una organización local posible es:

```text
Proyectos/
├── 00-ia-dos/
└── [Proyecto]/
    ├── [proyecto-app]/
    ├── [proyecto-wiki]/
    └── [proyecto-exch]/
```

Esta topología es opcional. No copies ni clones IA-DOS dentro de la aplicación o la Wiki del proyecto únicamente para cumplir el método.

Si la referencia local no existe:

1. usa el contrato embebido;
2. usa la fuente remota cuando esté disponible;
3. solicita autorización antes de clonar o crear una referencia local;
4. no realices un clon silencioso.

## Contrato de retorno

Todo artefacto debe comenzar con un encabezado suficiente para vincularlo con su tarea y receptor.

### Implementation Plan

```text
Artifact Type: Implementation Plan
Cycle ID: [CYCLE-ID O NO APLICA]
Planning Task ID: [PLAN-ID]
Agent Session: [IDENTIFICADOR CUANDO CORRESPONDA]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
Decisión requerida: Aprobar | Corregir | Rechazar | Escalar
```

### Execution Report

```text
Artifact Type: Execution Report
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Execution Cell o Agent Session: [NOMBRE CUANDO CORRESPONDA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Decisión requerida: APROBAR Y CERRAR | CORREGIR | REVERTIR | ESCALAR | REVISAR MEMORIA | NINGUNA
```

El estado describe el resultado ejecutado. La decisión requerida describe qué debe hacer después el Cycle Owner.

En Exchange v0 puede usarse `templates/exchange-report-v0.template.md`, que mantiene este mismo contrato semántico.

## Gate de revisión

Al recibir un Implementation Plan, el Cycle Owner no reinicia el diagnóstico. Comprueba evidencia, tamaño y seguridad, y aprueba o corrige una sola Execution Task candidata.

Al recibir un Execution Report, comprueba objetivo, alcance, criterios y evidencia. Luego cierra, emite una corrección acotada, revierte, inicia una nueva unidad o escala solo ante reorientación real.

## Regla principal

Cada intercambio debe conservar rol, autorización, identificadores y destino. Las conversaciones de ejecución pueden persistir; la autoridad de cada tarea no. Exchange no modifica el contrato semántico de los artefactos. El coding agent produce artefactos y el Conversation Space especialista toma decisiones.
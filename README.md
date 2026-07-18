# IA-DOS

**Intelligence-Assisted Development Operating System**

IA-DOS es un framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, planificación técnica, ejecución acotada, memoria durable y verificación basada en evidencia.

Su objetivo es mantener separados:

```text
dirección y decisión
≠ inspección técnica
≠ ejecución
≠ verificación
```

## Flujo actual

```text
Conversation Space orienta y gobierna
→ tarea tipada y compacta
→ coding agent planifica o ejecuta
→ artefacto verificable
→ Cycle Owner revisa y decide
```

`00` orienta prioridad y recibe solo reorientaciones o escalamiento real. El especialista que confirma el siguiente resultado se convierte en Cycle Owner.

## Tipos de artefacto

Cada bloque transferible declara su tipo, receptor y salida esperada:

- `Specialist Handoff` → Conversation Space;
- `Planning Task` → Coding Agent — Planning;
- `Implementation Plan` → Cycle Owner;
- `Execution Task` → Coding Agent — Execution;
- `Execution Report` → Cycle Owner.

Esto evita que una conversación especialista ejecute por error una tarea destinada al coding agent.

Consulta [Tipado de artefactos y validación del receptor](docs/orchestration/typed-artifact-routing.md).

## Planificación técnica

Cuando falta inspección o diseño:

```text
Planning Task
→ sesión PLAN — [RESULTADO]
→ coding agent en solo lectura
→ Implementation Plan
→ revisión del Cycle Owner
```

La salida operativa por defecto usa la [Planning Task compacta](templates/planning-task-compact.template.md). La [Planning Task completa](templates/planning-task.template.md) funciona como referencia de diseño y validación.

El plan debe cerrar una sola decisión técnica dominante y proponer una primera unidad segura. No debe convertirse por defecto en auditoría completa, arquitectura final o roadmap integral.

## Ejecución

Cuando el trabajo ya está definido y aprobado:

```text
Execution Task
→ sesión [RESULTADO]
→ coding agent ejecuta
→ Execution Report
→ revisión del Cycle Owner
```

La sesión de ejecución es independiente de la sesión de planificación. El coding agent no aprueba su propio resultado ni inicia automáticamente otra unidad.

## Roles y trazabilidad

Cada tarea dirigida a un coding agent declara:

- rol activo;
- Cycle ID;
- Task ID;
- Agent Session;
- Cycle Owner;
- artefacto de entrada;
- artefacto de salida;
- destino;
- autoridad.

Consulta [Roles, sesiones y ciclo de artefactos](docs/orchestration/agent-role-and-artifact-loop.md).

## Gate de tamaño y complejidad

Antes de aprobar una Execution Task:

```text
¿Puede una sola sesión implementarla, verificarla y reportarla
sin mezclar resultados independientes ni tomar decisiones mayores no resueltas?
```

Si no, se divide el plan y se aprueba solo la primera unidad.

## Aprobación comprensible

Antes de pedir una aprobación, el especialista debe resumir en lenguaje simple:

- qué cambiará;
- qué comportamiento quedará disponible;
- qué permisos se conceden;
- qué acciones externas pueden ocurrir;
- qué no está autorizado;
- cómo se verificará.

Una aprobación autoriza solo la Execution Task presentada, no el plan general.

## Empieza

1. Crea un Project, Gem, chat persistente o entorno equivalente.
2. Sigue [Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md).
3. Entrega una descripción breve y las fuentes disponibles.
4. Abre `00 — Dirección y definición` para un producto nuevo o `00 — Descubrimiento y adopción` para uno existente.
5. Avanza mediante tareas tipadas que regresan al Cycle Owner.

Cuando la plataforma no pueda navegar el repositorio, carga el [pack operativo](bundles/ia-dos-project-orchestrator-pack.md) y sus complementos obligatorios.

## Contratos principales

- [Project Orchestrator](ORCHESTRATOR.md)
- [Documentación](docs/index.md)
- [Registro de tópicos](docs/orchestration/topic-routing-registry.md)
- [Propiedad del ciclo](docs/orchestration/cycle-ownership.md)
- [Salida rápida](docs/orchestration/fast-planning-lane.md)
- [Tipado de artefactos](docs/orchestration/typed-artifact-routing.md)
- [Roles y sesiones](docs/orchestration/agent-role-and-artifact-loop.md)
- [Autoridad de fuentes y artefactos](docs/execution/source-and-artifact-authority.md)

## Plantillas principales

- [Project Intake Brief](templates/project-intake-brief.template.md)
- [Specialist Handoff](templates/conversation-space-handoff.template.md)
- [Planning Task compacta](templates/planning-task-compact.template.md)
- [Planning Task completa](templates/planning-task.template.md)
- [Project Start Planning Brief](templates/project-start-planning-brief.template.md)
- [Implementation Plan](templates/implementation-plan.template.md)
- [Execution Task](templates/execution-task.template.md)
- [Execution Report](templates/execution-report.template.md)

## Acceso al método

Las tareas pueden usar:

- `Embedded Contract`;
- `Remote Repository`;
- `Local Reference`.

Una referencia local compartida puede existir fuera del producto. IA-DOS no debe clonarse silenciosamente ni dentro del repositorio de la aplicación.

## Estado

IA-DOS está en fase alpha y se valida mediante proyectos reales antes de una release estable.

## Licencia

Apache License 2.0.

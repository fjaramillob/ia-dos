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
- `Environment Preflight` → Coding Agent — Planning;
- `Environment Readiness Report` → Cycle Owner;
- `Implementation Plan` → Cycle Owner;
- `Execution Task` → Coding Agent — Execution;
- `Execution Resume` → Coding Agent — Execution;
- `Execution Report` → Cycle Owner.

El mecanismo utilizado para transportar o almacenar un artefacto no crea otro tipo. Consulta [Tipado de artefactos y validación del receptor](docs/orchestration/typed-artifact-routing.md).

## Compresión de contexto por autoridad

IA-DOS evita reenviar la historia completa del proyecto en cada iteración.

```text
fuentes de autoridad
+ artefacto previo válido
+ delta del ciclo
+ contrato operativo explícito
```

- la memoria durable conserva contexto y decisiones estables;
- la implementación demuestra el estado técnico real;
- cada tarea transporta solo el cambio activo;
- permisos, límites, criterios y condiciones de detención permanecen explícitos;
- cuando una fuente no es accesible, se incluye solo el extracto indispensable.

Consulta [Compresión de contexto por autoridad](docs/orchestration/context-compression-by-authority.md).

## Planificación técnica

Cuando falta inspección o diseño:

```text
Planning Task
→ coding agent en solo lectura
→ Implementation Plan
→ revisión del Cycle Owner
```

La salida operativa por defecto usa la [Planning Task compacta](templates/planning-task-compact.template.md). La [Planning Task completa](templates/planning-task.template.md) funciona como referencia de diseño y validación.

El plan debe cerrar una sola decisión técnica dominante y proponer una primera unidad segura. No debe convertirse por defecto en auditoría completa, arquitectura final o roadmap integral.

IA-DOS conserva una frontera explícita entre planificación y ejecución, pero todavía no impone una política universal de persistencia o renovación de conversaciones de planificación.

## Ejecución

Cuando el trabajo ya está definido y aprobado:

```text
Execution Task
→ Execution Cell activa, cuando el proyecto usa ese modelo
→ coding agent ejecuta
→ Execution Report
→ revisión del Cycle Owner
```

Una `Execution Cell` conserva continuidad de ejecución para un flujo durable del proyecto. No representa una tarea ni una especialidad profesional. Cuando la herramienta permite conversaciones persistentes, se mantiene una sola conversación activa por célula mientras siga respondiendo bien.

Ejemplos posibles:

```text
App
Wiki Sync
```

La conversación puede renovarse por degradación o contaminación de contexto, pero la célula continúa. Los permisos no se acumulan entre tareas: cada `Execution Task` vuelve a declarar su autoridad.

Consulta [Execution Cells y Exchange Protocol v0](docs/execution/execution-cells-and-exchange.md).

## Un solo contrato de Execution Task

IA-DOS mantiene un único contrato semántico de ejecución.

```text
Execution Task
= objetivo + alcance + autoridad + permisos
+ criterios + verificaciones + condiciones de detención
```

Puede representarse con la [Execution Task compacta](templates/execution-task-compact.template.md), la [Execution Task completa](templates/execution-task.template.md) o el perfil [Exchange Execution Task v0](templates/exchange-task-v0.template.md).

Exchange no debilita el contrato: sólo aporta identificación autocontenida, persistencia y transporte manual.

## Exchange Protocol v0

Un proyecto puede mantener un almacén de instrucciones y respuestas:

```text
Proyecto/
├── proyecto-app/
├── proyecto-wiki/
└── proyecto-exch/
    ├── inbox/
    ├── outbox/
    ├── archive/
    └── templates/
```

Esta topología es opcional.

Exchange no sustituye la Wiki, el backlog ni el repositorio. Conserva el historial operacional de `TASK` y `REPORT` fuera de las conversaciones y permite reemplazar una conversación de coding agent sin perder el intercambio durable.

En v0, el intercambio es manual y puede usar como `Task ID`:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

El `REPORT` reutiliza exactamente el mismo `Task ID` del `TASK`. Cuando no existe un ciclo separado, `Cycle ID` puede declararse `NO APLICA`.

## Memoria durable portable

La Wiki conserva estado y decisiones vigentes; no debe convertirse en una copia de conversaciones o Execution Reports.

Cuando el proyecto utiliza una base Markdown local, IA-DOS recomienda que sea portable entre GitHub, editores, Obsidian y coding agents. Obsidian puede actuar como interfaz humana de navegación sin convertirse en una fuente de verdad separada.

El coding agent no lee toda la Wiki por defecto. Una tarea distingue entre contexto durable incluido, referencias para trazabilidad y lectura explícitamente requerida.

Consulta [Memoria durable portable y consumo desde Obsidian](docs/foundations/durable-memory-and-obsidian.md).

## Roles y trazabilidad

Cada tarea dirigida a un coding agent conserva suficiente información para identificar:

- rol activo;
- tarea o intercambio;
- Conversation Space que gobierna el resultado;
- Execution Cell o sesión cuando corresponda;
- artefacto de entrada;
- artefacto de salida;
- destino;
- autoridad.

Consulta [Roles, sesiones y ciclo de artefactos](docs/orchestration/agent-role-and-artifact-loop.md).

## Gate de tamaño y complejidad

Antes de aprobar una Execution Task:

```text
¿Puede una sola unidad implementarse, verificarse y reportarse
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
4. Abre `00 — Dirección y orquestación`; usa modo `definición inicial` para un producto nuevo o modo `descubrimiento y adopción` para uno existente.
5. Avanza mediante tareas tipadas que regresan al Cycle Owner.

Si la plataforma no puede navegar el repositorio canónico, usa como contrato offline mínimo `ORCHESTRATOR.md` junto con `templates/project-instructions.template.md`. No combines bundles heredados. El archivo `bundles/ia-dos-current-offline-pack.md` sólo debe utilizarse cuando su propio encabezado declare que está sincronizado con la versión o commit de IA-DOS adoptado.

## Contratos principales

- [Project Orchestrator](ORCHESTRATOR.md)
- [Documentación](docs/index.md)
- [Registro de tópicos](docs/orchestration/topic-routing-registry.md)
- [Propiedad del ciclo](docs/orchestration/cycle-ownership.md)
- [Salida rápida](docs/orchestration/fast-planning-lane.md)
- [Tipado de artefactos](docs/orchestration/typed-artifact-routing.md)
- [Roles y sesiones](docs/orchestration/agent-role-and-artifact-loop.md)
- [Execution Cells y Exchange v0](docs/execution/execution-cells-and-exchange.md)
- [Compresión de contexto](docs/orchestration/context-compression-by-authority.md)
- [Memoria durable portable](docs/foundations/durable-memory-and-obsidian.md)
- [Autoridad de fuentes y artefactos](docs/execution/source-and-artifact-authority.md)

## Plantillas principales

- [Project Intake Brief](templates/project-intake-brief.template.md)
- [Specialist Handoff](templates/conversation-space-handoff.template.md)
- [Planning Task compacta](templates/planning-task-compact.template.md)
- [Planning Task completa](templates/planning-task.template.md)
- [Project Start Planning Brief](templates/project-start-planning-brief.template.md)
- [Implementation Plan](templates/implementation-plan.template.md)
- [Execution Task compacta](templates/execution-task-compact.template.md)
- [Execution Task completa](templates/execution-task.template.md)
- [Execution Report](templates/execution-report.template.md)
- [Exchange Execution Task v0](templates/exchange-task-v0.template.md)
- [Exchange Execution Report v0](templates/exchange-report-v0.template.md)

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

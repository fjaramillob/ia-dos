# IA-DOS

**Intelligence-Assisted Development Operating System**

IA-DOS es un framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, memoria durable, planificación técnica, ejecución acotada y verificación basada en evidencia.

Coordina a la persona responsable, el Project Orchestrator, Conversation Spaces, coding agents, fuentes, artefactos, entornos y mecanismos de trazabilidad.

## Método de trabajo

```text
conversación 00
→ orientación y prioridad
→ tópico especializado solo si desbloquea una brecha
→ asignación de Cycle Owner
→ Planning Task o Execution Task
→ Implementation Plan o Execution Report
→ revisión en el destino declarado
→ iteración o escalamiento
```

`00` no es una parada obligatoria entre definición, planificación y ejecución.

IA-DOS no impone una topología concreta de carpetas, repositorios, servicios, herramientas o proveedores.

## Tres registros operativos

IA-DOS utiliza tres contratos complementarios:

- [Registro de tópicos conversacionales](docs/orchestration/topic-routing-registry.md): decide dónde resolver una brecha.
- [Propiedad y retorno del ciclo](docs/orchestration/cycle-ownership.md): decide quién gobierna el resultado y dónde vuelve cada artefacto.
- [Registro de tipos de ejecución](docs/execution/execution-task-types.md): decide cómo materializar una unidad aprobada.

Además, [Autoridad de fuentes, artefactos y entornos](docs/execution/source-and-artifact-authority.md) define qué demuestra cada recurso y qué acceso está permitido.

```text
tópico
→ dónde se razona

Cycle Owner
→ quién gobierna el resultado

Planning Task
→ cómo diseñar la implementación sin escribir

Execution Task
→ cómo materializar una unidad aprobada
```

## Empieza en cinco pasos

### 1. Crea el espacio conversacional del proyecto

Utiliza un Project, Gem, chat persistente o entorno equivalente.

### 2. Inicializa el Project Orchestrator

Sigue [Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md).

El primer chat queda identificado como:

- `00 — Dirección y definición` para un producto nuevo;
- `00 — Descubrimiento y adopción` para un producto existente.

### 3. Entrega las fuentes disponibles

Comparte una descripción breve, documentos, repositorios, servicios, una memoria existente o el [Project Intake Brief](templates/project-intake-brief.template.md).

Cuando la plataforma no pueda navegar este repositorio, carga el [IA-DOS Project Orchestrator Pack](bundles/ia-dos-project-orchestrator-pack.md).

### 4. Orienta y asigna propiedad

El Orchestrator debe:

- capturar propósito, usuario, problema y prioridad;
- identificar la decisión dominante;
- abrir solo el Conversation Space necesario;
- asignar un Cycle Owner;
- decidir entre planificación técnica y ejecución directa;
- devolver cada artefacto al destino declarado;
- escalar a `00` solo para reorientar.

### 5. Prepara el entorno solo cuando haga falta

Antes de planificar o ejecutar, identifica el entorno real, los recursos disponibles, el trabajo que debe preservarse y los permisos efectivos.

No prepares infraestructura ni impongas una estructura física por anticipación.

## Planning Task

Usa una Planning Task cuando el siguiente resultado requiera inspección o diseño técnico antes de autorizar escritura.

```text
Planning Task
→ coding agent en solo lectura
→ Implementation Plan
→ revisión del Cycle Owner
→ aprobación de una unidad
```

Plan producido no equivale a plan aprobado ni a ejecución autorizada.

## Gate de tamaño

Antes de aprobar una Execution Task:

```text
¿Puede completarse, verificarse y reportarse
como una sola unidad sin mezclar resultados independientes?
```

Si no, divide el plan y aprueba solo la primera unidad.

## Tópicos conversacionales bajo demanda

- `00 — Dirección y orquestación`;
- `10 — Producto y UX`;
- `20 — Arquitectura y stack`;
- `30 — Ejecución y desarrollo`;
- `40 — Calidad, seguridad y cumplimiento`;
- `50 — Operación y entrega`;
- `90 — Wiki y memoria`.

No constituyen etapas obligatorias.

## Tipos de ejecución

Toda `Execution Task` declara un tipo principal:

`INSPECT`, `BOOTSTRAP`, `BUILD`, `FIX`, `REFACTOR`, `MIGRATE`, `TEST`, `HARDEN`, `DOCUMENT`, `WIKI`, `RELEASE` u `OPERATE`.

La planificación se realiza mediante `Planning Task`; no es un tipo de materialización.

## Coding agents

Los coding agents pueden:

- inspeccionar en solo lectura y producir un Implementation Plan;
- materializar una Execution Task autorizada;
- ejecutar verificaciones;
- devolver el artefacto requerido al destino declarado.

No deben ampliar alcance ni tomar decisiones no autorizadas.

## Memoria durable

La memoria del proyecto conserva decisiones y estado confirmado. Las conversaciones y sesiones de coding agents no son memoria durable.

Las propuestas no deben registrarse como implementación.

## Accesos rápidos

- [Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md)
- [Consultar la documentación](docs/index.md)
- [Registro de tópicos](docs/orchestration/topic-routing-registry.md)
- [Propiedad del ciclo](docs/orchestration/cycle-ownership.md)
- [Avance concreto](docs/orchestration/concrete-execution-flow.md)
- [Autoridad de fuentes y artefactos](docs/execution/source-and-artifact-authority.md)
- [Planning Task](templates/planning-task.template.md)
- [Implementation Plan](templates/implementation-plan.template.md)
- [Execution Task](templates/execution-task.template.md)
- [Execution Report](templates/execution-report.template.md)

## Estado

IA-DOS está en fase alpha y se valida mediante proyectos reales antes de una release estable.

## Licencia

Apache License 2.0.
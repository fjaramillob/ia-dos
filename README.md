# IA-DOS

**Intelligence-Assisted Development Operating System**

IA-DOS es un framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, memoria durable, ejecución acotada y verificación basada en evidencia.

Coordina a la persona responsable, el Project Orchestrator, Conversation Spaces especializados, coding agents, repositorios de producto, LLM Wikis y fuentes de trazabilidad.

## Método de trabajo

```text
conversación 00
→ orientación y prioridad
→ tópico especializado solo si desbloquea una brecha
→ Execution Task clasificada
→ preparación local cuando la ejecución lo requiera
→ coding agent
→ Execution Report al espacio de origen
→ revisión e iteración
```

La instalación local no es el punto de partida. IA-DOS comienza en una conversación dirigida y prepara el entorno local cuando una tarea necesita repositorios, archivos, Git o un coding agent.

## Dos registros operativos

IA-DOS utiliza dos registros complementarios para evitar que cada asistente improvise la organización:

- [Registro de tópicos conversacionales](docs/orchestration/topic-routing-registry.md): decide dónde razonar, cuándo abrir un Conversation Space y qué salida debe producir.
- [Registro de tipos de ejecución](docs/execution/execution-task-types.md): decide cómo debe trabajar el coding agent, qué evidencia se espera y qué autorizaciones no se presumen.

```text
tópico conversacional
→ define dónde se resuelve la decisión

tipo de ejecución
→ define cómo se materializa el resultado
```

Los registros no crean una secuencia obligatoria. Aportan clasificación, defaults y gates de salida.

## Empieza en cinco pasos

### 1. Crea el espacio conversacional del proyecto

Utiliza un Project, Gem, chat persistente o entorno equivalente.

### 2. Inicializa el Project Orchestrator

Sigue [Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md).

El primer chat queda identificado como:

- `00 — Dirección y definición` para un producto nuevo;
- `00 — Descubrimiento y adopción` para un producto existente.

### 3. Entrega las fuentes disponibles

Comparte una descripción breve, documentos, repositorios, una Wiki existente o el [Project Intake Brief](templates/project-intake-brief.template.md).

Cuando la plataforma no pueda navegar este repositorio, carga el [IA-DOS Project Orchestrator Pack](bundles/ia-dos-project-orchestrator-pack.md).

### 4. Orienta y clasifica el siguiente resultado

El Orchestrator debe:

- capturar propósito, usuario, problema y prioridad;
- identificar la decisión dominante;
- enrutarla usando el registro de tópicos;
- abrir solo el Conversation Space que resuelva una brecha real;
- omitir conversaciones innecesarias;
- clasificar la tarea con un tipo de ejecución;
- preparar una `Execution Task` tan pronto exista claridad suficiente.

Consulta:

- [Iniciar un producto nuevo](docs/getting-started/new-project-from-conversation.md)
- [Adoptar un producto existente](docs/getting-started/adopt-existing-project-from-conversation.md)

### 5. Prepara el entorno local solo cuando haga falta ejecutar

Cuando la tarea requiera acceso real a repositorios, archivos, Git o herramientas locales, el Orchestrator debe indicar el paso correspondiente:

- [Preparar el workspace local](docs/getting-started/workspace-setup.md)
- [Instalar IA-DOS en el workspace](docs/getting-started/install-ia-dos.md)
- [Crear un proyecto nuevo en el workspace](docs/getting-started/create-new-project-workspace.md)
- [Incorporar un proyecto existente](docs/getting-started/incorporate-existing-project-workspace.md)
- [Preparar un handoff de ejecución](docs/getting-started/execution-handoff.md)

No prepares infraestructura local por anticipación si todavía no existe una tarea que la necesite.

## Tópicos conversacionales bajo demanda

- `00 — Dirección y orquestación`: prioridad, límites y reorientación;
- `10 — Producto y UX`: comportamiento, flujo y experiencia;
- `20 — Arquitectura y stack`: arquitectura, datos, integraciones y decisiones técnicas;
- `30 — Ejecución y desarrollo`: descomposición compleja, solo cuando aporta;
- `40 — Calidad, seguridad y cumplimiento`: validación y riesgo con contexto propio;
- `50 — Operación y entrega`: entornos, releases, observabilidad y continuidad;
- `90 — Wiki y memoria`: síntesis y gobierno documental complejo.

No constituyen etapas obligatorias. Consulta el registro antes de abrir un nuevo espacio.

## Tipos de ejecución

Toda `Execution Task` declara un tipo principal: `INSPECT`, `BOOTSTRAP`, `BUILD`, `FIX`, `REFACTOR`, `MIGRATE`, `TEST`, `HARDEN`, `DOCUMENT`, `WIKI`, `RELEASE` u `OPERATE`.

El tipo orienta el modo de trabajo, pero no concede permisos sobre escritura, Git, despliegue, datos, costes o producción.

## Coding agents

Los coding agents materializan tareas autorizadas, ejecutan verificaciones y devuelven un `Execution Report` al Conversation Space de origen. No deben ampliar alcance ni fusionar cambios sin autorización.

## LLM Wiki

La Wiki conserva memoria durable en Markdown y se puebla progresivamente. Puede actualizarse en la misma tarea que modifica el producto cuando el conocimiento sea claro y acotado.

## Accesos rápidos

- [Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md)
- [Consultar la documentación](docs/index.md)
- [Registro de tópicos conversacionales](docs/orchestration/topic-routing-registry.md)
- [Registro de tipos de ejecución](docs/execution/execution-task-types.md)
- [Avance concreto y transición a ejecución](docs/orchestration/concrete-execution-flow.md)
- [Trabajar con coding agents](docs/execution/coding-agents.md)

## Estado

IA-DOS está en fase alpha y se valida mediante proyectos reales antes de una release estable.

## Licencia

Apache License 2.0.
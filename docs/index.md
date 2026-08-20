# Documentación de IA-DOS

Esta documentación explica cómo utilizar IA-DOS para dirigir proyectos de software con asistentes conversacionales y coding agents sin perder contexto, control ni trazabilidad.

## Empieza aquí

La primera adopción sigue este orden:

1. [Inicializa el Project Orchestrator](../prompts/getting-started/initialize-project-orchestrator.md).
2. Entrega una descripción breve y las fuentes disponibles.
3. Abre `00 — Dirección y orquestación`; usa modo `definición inicial` para un producto nuevo o `descubrimiento y adopción` para uno existente.
4. Clasifica la brecha con el [Registro de tópicos](orchestration/topic-routing-registry.md), única lista normativa de Conversation Spaces.
5. Abre solo el Conversation Space que desbloquee el siguiente resultado.
6. Asigna un Cycle Owner con [Propiedad y retorno del ciclo](orchestration/cycle-ownership.md).
7. Decide entre `Planning Task`, `Environment Preflight`, `Execution Task` o `Execution Resume`.
8. Tipifica el bloque y valida el rol receptor.
9. Confirma la autoridad de fuentes, artefactos y entornos.
10. Si la siguiente unidad depende de historia conversacional, evalúa el [Memory Bootstrap Gate](foundations/memory-bootstrap-gate.md).
11. Aplica [Compresión de contexto por autoridad](orchestration/context-compression-by-authority.md).
12. Cuando exista ejecución recurrente, define sólo las [Execution Cells](execution/execution-cells-and-exchange.md) que aporten continuidad real.
13. Reutiliza la conversación activa de una Execution Cell mientras siga respondiendo bien; no abras una conversación por cada tarea.
14. Devuelve el artefacto al Cycle Owner declarado.
15. Escala a `00` sólo cuando exista reorientación real.

Si la plataforma no puede navegar el repositorio canónico, usa `ORCHESTRATOR.md` junto con `templates/project-instructions.template.md` como contrato offline mínimo. No combines bundles o addenda heredados para un onboarding nuevo. `bundles/ia-dos-current-offline-pack.md` sólo debe usarse cuando su encabezado declare sincronización con la versión o commit adoptado.

## Contratos operativos

- [Registro de tópicos conversacionales](orchestration/topic-routing-registry.md): gobierna dónde se resuelve cada decisión.
- [Propiedad y retorno del ciclo](orchestration/cycle-ownership.md): gobierna quién mantiene objetivo, límites y revisión.
- [Avance concreto y transición](orchestration/concrete-execution-flow.md): decide cuándo planificar y cuándo ejecutar.
- [Tipado de artefactos y validación del receptor](orchestration/typed-artifact-routing.md): define el contrato semántico de los artefactos independientemente de su transporte.
- [Roles, sesiones y ciclo de artefactos](orchestration/agent-role-and-artifact-loop.md): conserva identidad, permisos y retorno.
- [Execution Cells y Exchange Protocol v0](execution/execution-cells-and-exchange.md): reduce conversaciones de ejecución y conserva `TASK/REPORT` fuera del chat cuando aporte.
- [Compresión de contexto por autoridad](orchestration/context-compression-by-authority.md): separa referencias durables, delta y contrato operativo.
- [Memory Bootstrap Gate](foundations/memory-bootstrap-gate.md): evita depender de conocimiento que exista sólo en conversaciones.
- [Registro de tipos de ejecución](execution/execution-task-types.md): gobierna cómo se materializa una unidad aprobada.
- [Autoridad de fuentes, artefactos y entornos](execution/source-and-artifact-authority.md): gobierna qué demuestra cada recurso y qué acceso está permitido.

Estos contratos no crean una secuencia obligatoria ni imponen herramientas o estructuras físicas.

## Recorridos principales

- [Iniciar un producto nuevo desde conversación](getting-started/new-project-from-conversation.md)
- [Adoptar un producto existente desde conversación](getting-started/adopt-existing-project-from-conversation.md)
- [Avance concreto y transición a coding agents](orchestration/concrete-execution-flow.md)
- [Preparar y revisar un handoff técnico](getting-started/execution-handoff.md)

## Preparación del entorno, cuando corresponda

- [Preparar el workspace local](getting-started/workspace-setup.md)
- [Instalar IA-DOS](getting-started/install-ia-dos.md)
- [Crear un proyecto nuevo en el workspace](getting-started/create-new-project-workspace.md)
- [Incorporar un proyecto existente](getting-started/incorporate-existing-project-workspace.md)
- [Crear o conectar la memoria durable](getting-started/bootstrap-llm-wiki.md)
- [Aplicar las plantillas mínimas de adopción](getting-started/apply-starter-templates.md)

Estas guías son opciones de implementación, no requisitos normativos del método.

## Orquestación

- [IA-DOS Project Orchestrator](../ORCHESTRATOR.md)
- [Instrucciones persistentes](../templates/project-instructions.template.md)
- [Registro de tópicos](orchestration/topic-routing-registry.md)
- [Propiedad del ciclo](orchestration/cycle-ownership.md)
- [Tipado de artefactos](orchestration/typed-artifact-routing.md)
- [Roles y sesiones](orchestration/agent-role-and-artifact-loop.md)
- [Compresión de contexto](orchestration/context-compression-by-authority.md)
- [Conversation Space Handoff](../templates/conversation-space-handoff.template.md)
- [`90 — Wiki y memoria`](orchestration/wiki-and-memory.md)

El [Current Offline Pack](../bundles/ia-dos-current-offline-pack.md) se conserva como artefacto de distribución, pero no debe tratarse como vigente hasta que su encabezado confirme sincronización con la versión adoptada.

## Planificación

- [Planning Task compacta](../templates/planning-task-compact.template.md)
- [Planning Task completa](../templates/planning-task.template.md)
- [Project Start Planning Brief](../templates/project-start-planning-brief.template.md)
- [Implementation Plan](../templates/implementation-plan.template.md)
- [Autoridad de fuentes, artefactos y entornos](execution/source-and-artifact-authority.md)

La plantilla compacta es la salida operativa por defecto para pegar en el coding agent. La plantilla completa funciona como referencia de diseño, validación y casos excepcionales.

La política de persistencia o renovación de conversaciones de planificación se mantiene separada de la política de Execution Cells hasta que exista una decisión explícita.

## Ejecución

- [Registro de tipos de ejecución](execution/execution-task-types.md)
- [Coding agents](execution/coding-agents.md)
- [Execution Cells y Exchange Protocol v0](execution/execution-cells-and-exchange.md)
- [Execution Task compacta](../templates/execution-task-compact.template.md)
- [Execution Task completa](../templates/execution-task.template.md)
- [Execution Report](../templates/execution-report.template.md)
- [Exchange Task v0](../templates/exchange-task-v0.template.md)
- [Exchange Report v0](../templates/exchange-report-v0.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Actualizar la memoria durable](execution/updating-the-llm-wiki.md)
- [Entregar una tarea a un coding agent](../prompts/execution/handoff-to-coding-agent.md)

La Execution Task compacta y la completa representan el mismo contrato semántico con distinto nivel de detalle. Exchange v0 añade identificación y persistencia manual del par `TASK/REPORT`, pero no crea una Execution Task diferente. `Wiki Update Task` es un perfil documental de la misma Execution Task canónica.

## Fundamentos

- [Propósito y alcance](foundations/purpose-and-scope.md)
- [Método de trabajo](foundations/working-method.md)
- [Modelo operativo](foundations/operating-model.md)
- [Modelo de adopción](foundations/adoption-model.md)
- [Fuentes de verdad](foundations/source-of-truth.md)
- [Responsabilidades humanas y de la IA](foundations/human-ai-responsibilities.md)
- [Memory Bootstrap Gate](foundations/memory-bootstrap-gate.md)
- [Memoria durable portable y Obsidian](foundations/durable-memory-and-obsidian.md)
- [Terminología](foundations/terminology.md)
- [Criterios editoriales](foundations/editorial-guidelines.md)

## Integraciones y capacidades

- [Índice de integraciones](integrations/README.md)
- [Conectores y MCP](integrations/connectors-and-mcp.md)
- [Modelo de capacidades](integrations/capability-model.md)
- [Capability Manifest](../templates/capability-manifest.template.yaml)

## Plantillas

- [Project Intake Brief](../templates/project-intake-brief.template.md)
- [Conversation Space Handoff](../templates/conversation-space-handoff.template.md)
- [Instrucciones persistentes](../templates/project-instructions.template.md)
- [Planning Task compacta](../templates/planning-task-compact.template.md)
- [Planning Task completa](../templates/planning-task.template.md)
- [Implementation Plan](../templates/implementation-plan.template.md)
- [Execution Task compacta](../templates/execution-task-compact.template.md)
- [Execution Task completa](../templates/execution-task.template.md)
- [Exchange Task v0](../templates/exchange-task-v0.template.md)
- [Exchange Report v0](../templates/exchange-report-v0.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Execution Report](../templates/execution-report.template.md)
- [Adoption Manifest](../templates/adoption.template.yaml)
- [Wiki Starter](../templates/wiki-starter/00-home.md)

## Estado

IA-DOS está en fase alpha. Su método se valida y consolida mediante proyectos reales antes de publicarse como release estable.

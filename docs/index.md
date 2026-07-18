# Documentación de IA-DOS

Esta documentación explica cómo utilizar IA-DOS para dirigir proyectos de software con asistentes conversacionales y coding agents sin perder contexto, control ni trazabilidad.

## Empieza aquí

La primera adopción sigue este orden:

1. [Inicializa el Project Orchestrator](../prompts/getting-started/initialize-project-orchestrator.md).
2. Entrega una descripción breve y las fuentes disponibles.
3. Abre `00 — Dirección y definición` o `00 — Descubrimiento y adopción`.
4. Clasifica la brecha con el [Registro de tópicos](orchestration/topic-routing-registry.md).
5. Abre solo el Conversation Space que desbloquee el siguiente resultado.
6. Asigna un Cycle Owner con [Propiedad y retorno del ciclo](orchestration/cycle-ownership.md).
7. Decide entre `Planning Task` y `Execution Task`.
8. Tipifica el bloque y valida el rol receptor.
9. Confirma la autoridad de fuentes, artefactos y entornos.
10. Devuelve el `Implementation Plan` o `Execution Report` al destino declarado.
11. Escala a `00` solo cuando exista reorientación real.

## Contratos operativos

- [Registro de tópicos conversacionales](orchestration/topic-routing-registry.md): gobierna dónde se resuelve cada decisión.
- [Propiedad y retorno del ciclo](orchestration/cycle-ownership.md): gobierna quién mantiene objetivo, límites y revisión.
- [Avance concreto y transición](orchestration/concrete-execution-flow.md): decide cuándo planificar y cuándo ejecutar.
- [Tipado de artefactos y validación del receptor](orchestration/typed-artifact-routing.md): evita entregar un artefacto al rol equivocado.
- [Roles, sesiones y ciclo de artefactos](orchestration/agent-role-and-artifact-loop.md): conserva identidad, permisos y retorno.
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
- [Crear o revisar la LLM Wiki](getting-started/bootstrap-llm-wiki.md)

Estas guías son opciones de implementación, no requisitos normativos del método.

## Orquestación

- [IA-DOS Project Orchestrator](../ORCHESTRATOR.md)
- [Pack operativo](../bundles/ia-dos-project-orchestrator-pack.md)
- [Registro de tópicos](orchestration/topic-routing-registry.md)
- [Propiedad y retorno del ciclo](orchestration/cycle-ownership.md)
- [Tipado de artefactos](orchestration/typed-artifact-routing.md)
- [Roles y sesiones](orchestration/agent-role-and-artifact-loop.md)
- [Instrucciones persistentes](../templates/project-instructions.template.md)
- [Conversation Space Handoff](../templates/conversation-space-handoff.template.md)
- [`90 — Wiki y memoria`](orchestration/wiki-and-memory.md)

## Planificación

- [Planning Task compacta](../templates/planning-task-compact.template.md)
- [Planning Task completa](../templates/planning-task.template.md)
- [Project Start Planning Brief](../templates/project-start-planning-brief.template.md)
- [Implementation Plan](../templates/implementation-plan.template.md)
- [Autoridad de fuentes, artefactos y entornos](execution/source-and-artifact-authority.md)

La plantilla compacta es la salida operativa por defecto para pegar en el coding agent. La plantilla completa funciona como referencia de diseño, validación y casos excepcionales.

## Ejecución

- [Registro de tipos de ejecución](execution/execution-task-types.md)
- [Coding agents](execution/coding-agents.md)
- [Execution Task](../templates/execution-task.template.md)
- [Execution Report](../templates/execution-report.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Actualizar la LLM Wiki](execution/updating-the-llm-wiki.md)
- [Entregar una tarea a un coding agent](../prompts/execution/handoff-to-coding-agent.md)

## Fundamentos

- [Propósito y alcance](foundations/purpose-and-scope.md)
- [Método de trabajo](foundations/working-method.md)
- [Modelo operativo](foundations/operating-model.md)
- [Modelo de adopción](foundations/adoption-model.md)
- [Fuentes de verdad](foundations/source-of-truth.md)
- [Responsabilidades humanas y de la IA](foundations/human-ai-responsibilities.md)
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
- [Execution Task](../templates/execution-task.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Execution Report](../templates/execution-report.template.md)

## Estado

IA-DOS está en fase alpha. Su método se valida y consolida mediante proyectos reales antes de publicarse como release estable.

# Documentación de IA-DOS

Esta documentación explica cómo utilizar IA-DOS para dirigir proyectos de software con asistentes conversacionales y coding agents sin perder contexto, control ni trazabilidad.

## Empieza aquí

Para una primera adopción:

1. [Inicializa el Project Orchestrator](../prompts/getting-started/initialize-project-orchestrator.md).
2. Carga [IA-DOS Project Orchestrator Pack](../bundles/ia-dos-project-orchestrator-pack.md) cuando la plataforma no pueda navegar GitHub.
3. Entrega una descripción del proyecto o usa [Project Intake Brief](../templates/project-intake-brief.template.md).
4. Sigue el recorrido de [proyecto nuevo](getting-started/new-project-from-conversation.md) o [proyecto existente](getting-started/adopt-existing-project-from-conversation.md).
5. Crea o revisa la [LLM Wiki](getting-started/bootstrap-llm-wiki.md).
6. Convierte el siguiente cambio en una tarea acotada y materialízalo con un coding agent.

## Fundamentos

- [Propósito y alcance](foundations/purpose-and-scope.md)
- [Público objetivo](foundations/target-audience.md)
- [Principios](foundations/principles.md)
- [Método de trabajo](foundations/working-method.md)
- [Capa de orquestación conversacional](foundations/orchestration-layer.md)
- [Guía conversacional y autoridad de fuentes](foundations/conversational-guidance.md)
- [Modelo operativo](foundations/operating-model.md)
- [Modelo de adopción](foundations/adoption-model.md)
- [Fuentes de verdad](foundations/source-of-truth.md)
- [Responsabilidades humanas y de la IA](foundations/human-ai-responsibilities.md)
- [Terminología](foundations/terminology.md)
- [Versionado](foundations/versioning.md)
- [Criterios editoriales y sanitización pública](foundations/editorial-guidelines.md)

## Orquestación

- [IA-DOS Project Orchestrator](../ORCHESTRATOR.md)
- [`90 — Wiki y memoria`](orchestration/wiki-and-memory.md)
- [Prompt para inicializar el Project Orchestrator](../prompts/getting-started/initialize-project-orchestrator.md)
- [Pack para plataformas sin acceso al repositorio](../bundles/ia-dos-project-orchestrator-pack.md)
- [Plantilla opcional de instrucciones persistentes](../templates/project-instructions.template.md)
- [Conversation Space Handoff](../templates/conversation-space-handoff.template.md)

## Ejecución

- [Coding agents](execution/coding-agents.md)
- [Actualizar la LLM Wiki](execution/updating-the-llm-wiki.md)
- [Execution Task](../templates/execution-task.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Execution Report](../templates/execution-report.template.md)
- [Preparar y revisar el handoff](getting-started/execution-handoff.md)
- [Entregar una tarea a un coding agent](../prompts/execution/handoff-to-coding-agent.md)
- [Entregar una actualización de wiki](../prompts/execution/update-llm-wiki.md)

## Primeros pasos

- [Iniciar un proyecto nuevo](getting-started/new-project-from-conversation.md)
- [Adoptar un proyecto existente](getting-started/adopt-existing-project-from-conversation.md)
- [Crear la LLM Wiki](getting-started/bootstrap-llm-wiki.md)
- [Preparar el workspace local](getting-started/workspace-setup.md)
- [Instalar IA-DOS](getting-started/install-ia-dos.md)
- [Crear un proyecto nuevo en el workspace](getting-started/create-new-project-workspace.md)
- [Incorporar un proyecto existente](getting-started/incorporate-existing-project-workspace.md)
- [Aplicar plantillas mínimas](getting-started/apply-starter-templates.md)

## Prompts operativos

- [Instalar IA-DOS con un agente](../prompts/getting-started/install-ia-dos.md)
- [Crear un proyecto nuevo](../prompts/getting-started/create-new-project-workspace.md)
- [Incorporar un proyecto existente](../prompts/getting-started/incorporate-existing-project-workspace.md)
- [Entregar una tarea a un coding agent](../prompts/execution/handoff-to-coding-agent.md)
- [Actualizar la LLM Wiki con un coding agent](../prompts/execution/update-llm-wiki.md)

## Plantillas

- [Project Intake Brief](../templates/project-intake-brief.template.md)
- [Conversation Space Handoff](../templates/conversation-space-handoff.template.md)
- [Manifiesto de adopción](../templates/adoption.template.yaml)
- [AGENTS.md para la app](../templates/AGENTS.template.md)
- [Instrucciones persistentes](../templates/project-instructions.template.md)
- [Wiki inicial](../templates/wiki-starter/)
- [Execution Task](../templates/execution-task.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Execution Report](../templates/execution-report.template.md)

## Estado

IA-DOS está en fase alpha. Su método se valida y consolida mediante proyectos reales antes de publicarse como release estable.
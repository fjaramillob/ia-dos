# Documentación de IA-DOS

Esta documentación explica cómo utilizar IA-DOS para dirigir proyectos de software con asistentes conversacionales y coding agents sin perder contexto, control ni trazabilidad.

## Empieza aquí

La primera adopción sigue este orden:

1. [Inicializa el Project Orchestrator](../prompts/getting-started/initialize-project-orchestrator.md).
2. Entrega una descripción breve, documentos, repositorios o usa [Project Intake Brief](../templates/project-intake-brief.template.md).
3. Abre `00 — Dirección y definición` o `00 — Descubrimiento y adopción`.
4. Organiza solo las conversaciones que desbloqueen el siguiente resultado.
5. Prepara una `Execution Task` cuando exista claridad suficiente.
6. Instala o prepara el entorno local solo cuando la ejecución necesite repositorios, archivos, Git o un coding agent.
7. Devuelve el `Execution Report` al espacio que originó la tarea.

## Recorridos principales

- [Iniciar un producto nuevo desde conversación](getting-started/new-project-from-conversation.md)
- [Adoptar un producto existente desde conversación](getting-started/adopt-existing-project-from-conversation.md)
- [Avance concreto y transición a coding agents](orchestration/concrete-execution-flow.md)
- [Preparar y revisar el handoff de ejecución](getting-started/execution-handoff.md)

## Preparación local, cuando corresponda

- [Preparar el workspace local](getting-started/workspace-setup.md)
- [Instalar IA-DOS](getting-started/install-ia-dos.md)
- [Crear un proyecto nuevo en el workspace](getting-started/create-new-project-workspace.md)
- [Incorporar un proyecto existente](getting-started/incorporate-existing-project-workspace.md)
- [Crear o revisar la LLM Wiki](getting-started/bootstrap-llm-wiki.md)

Estas guías no son requisitos previos para iniciar el onboarding conversacional.

## Orquestación

- [IA-DOS Project Orchestrator](../ORCHESTRATOR.md)
- [Pack operativo](../bundles/ia-dos-project-orchestrator-pack.md)
- [Instrucciones persistentes](../templates/project-instructions.template.md)
- [Conversation Space Handoff](../templates/conversation-space-handoff.template.md)
- [`90 — Wiki y memoria`](orchestration/wiki-and-memory.md)

## Ejecución

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
- [Wiki inicial](../templates/wiki-starter/)
- [Execution Task](../templates/execution-task.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Execution Report](../templates/execution-report.template.md)

## Estado

IA-DOS está en fase alpha. Su método se valida y consolida mediante proyectos reales antes de publicarse como release estable.

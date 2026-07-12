# Documentación de IA-DOS

Esta documentación explica cómo utilizar IA-DOS para ordenar proyectos de software desarrollados con asistentes conversacionales y coding agents.

## Fundamentos

- [Propósito y alcance](foundations/purpose-and-scope.md)
- [Público objetivo](foundations/target-audience.md)
- [Principios](foundations/principles.md)
- [Capa de orquestación conversacional](foundations/orchestration-layer.md)
- [Modelo operativo](foundations/operating-model.md)
- [Modelo de adopción](foundations/adoption-model.md)
- [Fuentes de verdad](foundations/source-of-truth.md)
- [Responsabilidades humanas y de la IA](foundations/human-ai-responsibilities.md)
- [Terminología](foundations/terminology.md)
- [Versionado](foundations/versioning.md)

## Instrucciones para asistentes

- [IA-DOS Project Orchestrator](../ORCHESTRATOR.md)
- [Prompt para inicializar el Project Orchestrator](../prompts/getting-started/initialize-project-orchestrator.md)

Estos archivos permiten que ChatGPT, Gemini, Claude u otro asistente comprenda cómo debe coordinar conversaciones, wiki, tareas y coding agents.

## Primeros pasos

- [Iniciar un proyecto nuevo desde la capa conversacional](getting-started/new-project-from-conversation.md)
- [Adoptar un proyecto existente desde la capa conversacional](getting-started/adopt-existing-project-from-conversation.md)
- [Crear la LLM Wiki del proyecto](getting-started/bootstrap-llm-wiki.md)
- [Preparar el workspace local](getting-started/workspace-setup.md)
- [Instalar IA-DOS en el workspace](getting-started/install-ia-dos.md)
- [Crear un proyecto nuevo dentro del workspace](getting-started/create-new-project-workspace.md)
- [Incorporar un proyecto existente al workspace](getting-started/incorporate-existing-project-workspace.md)
- [Aplicar las plantillas mínimas de adopción](getting-started/apply-starter-templates.md)

## Prompts operativos

- [Instalar IA-DOS con un agente](../prompts/getting-started/install-ia-dos.md)
- [Crear un proyecto nuevo dentro del workspace](../prompts/getting-started/create-new-project-workspace.md)
- [Incorporar un proyecto existente al workspace](../prompts/getting-started/incorporate-existing-project-workspace.md)

## Plantillas

- [Manifiesto de adopción](../templates/adoption.template.yaml)
- [AGENTS.md para la app](../templates/AGENTS.template.md)
- [Wiki inicial](../templates/wiki-starter/)

Las guías de `Execution Task`, reporte de ejecución y verificación completa se incorporarán en los siguientes incrementos de `v0.1.0-alpha.1`.

## Estado de la documentación

IA-DOS está en fase alpha. Los documentos actuales definen la base conceptual, el recorrido conversacional, la preparación del workspace, la incorporación formal de proyectos y las plantillas mínimas de adopción. Todavía no constituyen una versión estable.

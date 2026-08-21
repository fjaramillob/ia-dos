# Documentación de IA-DOS

Esta documentación explica cómo utilizar IA-DOS para dirigir proyectos de software con asistentes conversacionales y coding agents sin perder contexto, control ni trazabilidad.

## Empieza aquí

La adopción sigue este orden conceptual, sin convertirse en una pipeline rígida:

1. [Inicializa el Project Orchestrator](../prompts/getting-started/initialize-project-orchestrator.md).
2. Entrega una descripción breve y las fuentes disponibles.
3. Comienza en `00 — Dirección y orquestación`; usa `definición inicial` para producto nuevo o `descubrimiento y adopción` para existente.
4. Abre sólo el Conversation Space que desbloquee el siguiente resultado, usando el [Registro de tópicos](orchestration/topic-routing-registry.md).
5. Asigna un Cycle Owner con [Propiedad y retorno del ciclo](orchestration/cycle-ownership.md).
6. Si la siguiente unidad depende de historia conversacional, evalúa primero el [Memory Bootstrap Gate](foundations/memory-bootstrap-gate.md).
7. Si una futura ejecución depende de readiness indispensable no comprobado, usa [Environment Preflight](execution/environment-readiness-and-resume.md).
8. Si falta inspección o diseño técnico, usa `Planning Task`; si la unidad ya está lista, usa `Execution Task`.
9. Tipifica el bloque y valida el receptor con [Tipado de artefactos](orchestration/typed-artifact-routing.md).
10. Confirma [autoridad de fuentes, artefactos y entornos](execution/source-and-artifact-authority.md).
11. Aplica [Compresión de contexto por autoridad](orchestration/context-compression-by-authority.md).
12. Cuando exista ejecución recurrente, define sólo las [Execution Cells](execution/execution-cells-and-exchange.md) que aporten continuidad real.
13. Reutiliza una Execution Cell mientras siga respondiendo bien; no abras una conversación por tarea.
14. Usa [Exchange](getting-started/bootstrap-exchange.md) sólo cuando una pasarela pasiva de Markdown aporte valor.
15. Devuelve planes, readiness reports y Execution Reports al Cycle Owner declarado.
16. La persona responsable conserva la aprobación final cuando la decisión excede la autoridad delegada.
17. Escala a `00` sólo ante reorientación real.

Si la plataforma no puede navegar el repositorio canónico, usa el [Current Offline Pack](../bundles/ia-dos-current-offline-pack.md) cuando declare `Estado: VIGENTE` y baseline canónico. Es el único bundle actual para nuevos onboardings offline. No combines bundles históricos; consulta [Bundles](../bundles/README.md).

## Contratos operativos

- [IA-DOS Project Orchestrator](../ORCHESTRATOR.md)
- [Registro de tópicos conversacionales](orchestration/topic-routing-registry.md)
- [Propiedad y retorno del ciclo](orchestration/cycle-ownership.md)
- [Avance concreto y transición](orchestration/concrete-execution-flow.md)
- [Tipado de artefactos](orchestration/typed-artifact-routing.md)
- [Roles, sesiones y ciclo de artefactos](orchestration/agent-role-and-artifact-loop.md)
- [Compresión de contexto por autoridad](orchestration/context-compression-by-authority.md)
- [Memory Bootstrap Gate](foundations/memory-bootstrap-gate.md)
- [Execution Cells y Exchange](execution/execution-cells-and-exchange.md)
- [Readiness y Execution Resume](execution/environment-readiness-and-resume.md)
- [Autoridad de fuentes, artefactos y entornos](execution/source-and-artifact-authority.md)
- [Coding agents](execution/coding-agents.md)

Estos contratos no imponen herramientas, topología física o secuencia fija.

## Recorridos principales

- [Iniciar un producto nuevo desde conversación](getting-started/new-project-from-conversation.md)
- [Adoptar un producto existente desde conversación](getting-started/adopt-existing-project-from-conversation.md)
- [Avance concreto y transición a coding agents](orchestration/concrete-execution-flow.md)
- [Preparar y revisar un handoff técnico](getting-started/execution-handoff.md)
- [Validación end-to-end histórica de Fase 6](validation/end-to-end-onboarding-validation.md)
- [Revisión integral histórica de Fase 6](validation/final-integral-review.md)
- [Auditoría integral vigente del repositorio](validation/repository-integral-audit-2026-08-21.md)

## Preparación del entorno, cuando corresponda

- [Preparar el workspace local](getting-started/workspace-setup.md)
- [Instalar IA-DOS](getting-started/install-ia-dos.md)
- [Crear un proyecto nuevo en el workspace](getting-started/create-new-project-workspace.md)
- [Incorporar un proyecto existente](getting-started/incorporate-existing-project-workspace.md)
- [Crear o conectar la memoria durable](getting-started/bootstrap-llm-wiki.md)
- [Crear o conectar Exchange](getting-started/bootstrap-exchange.md)
- [Aplicar plantillas de adopción](getting-started/apply-starter-templates.md)

Estas guías son opciones de implementación, no requisitos normativos.

## Planificación y readiness

- [Planning Task compacta](../templates/planning-task-compact.template.md)
- [Planning Task completa](../templates/planning-task.template.md)
- [Project Start Planning Brief](../templates/project-start-planning-brief.template.md)
- [Implementation Plan](../templates/implementation-plan.template.md)
- [Environment Preflight](../templates/environment-preflight.template.md)
- [Environment Readiness Report](../templates/environment-readiness-report.template.md)

La política de conversaciones de Planning permanece abierta. Un identificador `PLAN — ...` no obliga a abrir una conversación por tarea.

## Ejecución

- [Execution Task compacta](../templates/execution-task-compact.template.md)
- [Execution Task completa](../templates/execution-task.template.md)
- [Execution Resume](../templates/execution-resume.template.md)
- [Execution Report](../templates/execution-report.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Actualizar la memoria durable](execution/updating-the-llm-wiki.md)
- [Entregar una tarea a un coding agent](../prompts/execution/handoff-to-coding-agent.md)

Una Execution Cell conserva continuidad, no permisos. Cada Execution Task vuelve a declarar autoridad completa.

El Execution Report es evidencia y no selecciona la decisión de gobierno posterior ni la memoria a consolidar.

## Memoria durable

- [Memory Bootstrap Gate](foundations/memory-bootstrap-gate.md)
- [Memoria durable portable y LLM Wiki](foundations/durable-memory-and-obsidian.md)
- [Crear o conectar la memoria durable](getting-started/bootstrap-llm-wiki.md)
- [Wiki Starter](../templates/wiki-starter/00-home.md)

`memoria durable` describe la función; `LLM Wiki` es una posible materialización portable y navegable.

## Fundamentos

- [Propósito y alcance](foundations/purpose-and-scope.md)
- [Principios](foundations/principles.md)
- [Modelo operativo](foundations/operating-model.md)
- [Modelo de adopción](foundations/adoption-model.md)
- [Fuentes de verdad](foundations/source-of-truth.md)
- [Responsabilidades humanas y de la IA](foundations/human-ai-responsibilities.md)
- [Terminología](foundations/terminology.md)
- [Checklist de revisión](foundations/review-checklist.md)
- [Preguntas de validación](foundations/validation-questions.md)

## Integraciones y capacidades

- [Índice de integraciones](integrations/README.md)
- [Conectores y MCP](integrations/connectors-and-mcp.md)
- [Modelo de capacidades](integrations/capability-model.md)
- [Capability Manifest](../templates/capability-manifest.template.yaml)

## Estado

IA-DOS está en etapa **alpha de adopción en proyectos reales**. Consulta [ROADMAP.md](../ROADMAP.md).

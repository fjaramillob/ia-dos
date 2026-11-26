# Documentación de IA-DOS

Esta documentación explica cómo utilizar IA-DOS para dirigir proyectos de software con asistentes conversacionales y coding agents sin perder contexto, control ni trazabilidad.

## Empieza aquí

La adopción sigue este orden conceptual, sin convertirse en una pipeline rígida:

1. Resuelve `Method Resolution Policy: FOLLOW_CURRENT | PINNED`; una mención conversacional de versión/SHA no constituye un pin durable.
2. Elige `Execution Entry Mode: ORCHESTRATED | DIRECT` según la necesidad actual.
3. En `ORCHESTRATED`, [inicializa o retoma el Project Orchestrator](../prompts/getting-started/initialize-project-orchestrator.md); en `DIRECT`, entrega la intención humana al Coding Agent y aplica [Direct Execution y Workspace Governance](execution/direct-execution-and-workspace-governance.md).
5. Entrega sólo la descripción y fuentes necesarias; no reconstruyas todo el proyecto por rutina.
4. Si usas Conversation Spaces, abre sólo el que desbloquee una decisión material y usa [Specialist Handoff](orchestration/topic-routing-registry.md) cuando realmente transfieras gobierno.
6. Si falta memoria durable indispensable, evalúa [Memory Bootstrap Gate](foundations/memory-bootstrap-gate.md).
7. Define o reconstruye Protected Invariants, Adaptation Authority y Protected Boundaries con [Ejecución adaptativa](execution/adaptive-execution.md).
8. Usa `Planning Task` sólo ante una decisión material no resuelta y `Environment Preflight` sólo cuando readiness deba conocerse antes de una frontera sensible.
9. En DIRECT, ejecuta sólo si `Direct Execution Gate = PASS`; si falta gobierno devuelve `NEEDS_GOVERNANCE`.
10. Confirma [autoridad de fuentes, artefactos y entornos](execution/source-and-artifact-authority.md).
11. Aplica [Compresión de contexto por autoridad](orchestration/context-compression-by-authority.md).
12. Usa Execution Cells sólo cuando aporten continuidad real; no abras una conversación por tarea.
13. Usa Exchange sólo cuando una pasarela pasiva de Markdown aporte valor; Exchange no es workflow ni router.
14. En ORCHESTRATED, devuelve evidencia al Cycle Owner; en DIRECT, deja continuidad durable suficiente para que el proyecto no dependa de la conversación del agente.
15. Si dirección, roadmap vigente, invariantes, fronteras y autoridad siguen estables, continúa sin microaprobaciones.
16. La persona responsable interviene cuando aparece una decisión material o cambia una frontera.
17. Reingresa Conversation Space / `00` sólo cuando exista un Governance Re-entry Trigger real.

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
- [Ejecución adaptativa y fronteras protegidas](execution/adaptive-execution.md)
- [Direct Execution y Workspace Governance](execution/direct-execution-and-workspace-governance.md)
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
- [Auditoría integral vigente del repositorio — 2026-11-25 / C08](validation/repository-integral-audit-2026-11-25-c08.md)
- [Auditoría integral histórica — 2026-11-25 / C07](validation/repository-integral-audit-2026-11-25.md)
- [Auditoría integral histórica — 2026-10-26 / C04](validation/repository-integral-audit-2026-10-26.md)
- [Auditoría integral histórica — 2026-08-21](validation/repository-integral-audit-2026-08-21.md)

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
- [Mapa opcional de proyecto/workspace](../templates/project-map.template.md)
- [Wiki Update Task](../templates/wiki-update-task.template.md)
- [Actualizar la memoria durable](execution/updating-the-llm-wiki.md)
- [Entregar una tarea a un coding agent](../prompts/execution/handoff-to-coding-agent.md)
- [Operar directamente bajo IA-DOS](../prompts/execution/direct-execution-under-ia-dos.md)

Una Execution Cell conserva continuidad, no permisos. Cada Execution Task vuelve a declarar autoridad completa.

El Execution Report es evidencia y no selecciona la decisión de gobierno posterior. Cuando la Task define Memory Policy, reporta el impacto durable real y el estado del Operational Baseline.

## Memoria durable

- [Memory Bootstrap Gate](foundations/memory-bootstrap-gate.md)
- [Memoria durable portable y LLM Wiki](foundations/durable-memory-and-obsidian.md)
- [Custodia de memoria estructural](foundations/memory-stewardship.md)
- [Crear o conectar la memoria durable](getting-started/bootstrap-llm-wiki.md)
- [Wiki Starter](../templates/wiki-starter/00-home.md)

`memoria durable` describe la función; `LLM Wiki` es una posible materialización portable y navegable.

La memoria semántica es selectiva (`NONE | CONDITIONAL | REQUIRED`). Cuando el proyecto adopta `90 — Documentación y memoria`, `Memory Stewardship: 90_STRUCTURAL` deriva sólo los cambios estructurales a ese custodio; baseline y memoria local no convierten a 90 en peaje operativo. En proyectos publicados con Wiki, el `Operational Baseline` conserva el último estado verificado para que un agente nuevo identifique repo/branch, HEAD remoto, commit productivo, deployment/release y entorno antes de revalidarlos. La superficie caliente de memoria debe además mostrar outcomes activos, milestones/capabilities relevantes, blockers y próximos horizontes ya aceptados; varios `DEFERRED` se consolidan cuando su efecto acumulado vuelve esa representación materialmente incompleta.

## Fundamentos

- [Propósito y alcance](foundations/purpose-and-scope.md)
- [Principios](foundations/principles.md)
- [Modelo operativo](foundations/operating-model.md)
- [Modelo de adopción](foundations/adoption-model.md)
- [Fuentes de verdad](foundations/source-of-truth.md)
- [Responsabilidades humanas y de la IA](foundations/human-ai-responsibilities.md)
- [Terminología](foundations/terminology.md)
- [Versionado y Method Resolution](foundations/versioning.md)
- [Checklist de revisión](foundations/review-checklist.md)
- [Preguntas de validación](foundations/validation-questions.md)

## Integraciones y capacidades

- [Índice de integraciones](integrations/README.md)
- [Conectores y MCP](integrations/connectors-and-mcp.md)
- [Modelo de capacidades](integrations/capability-model.md)
- [Capability Manifest](../templates/capability-manifest.template.yaml)

## Estado

IA-DOS está en etapa **alpha de adopción en proyectos reales**. Consulta [ROADMAP.md](../ROADMAP.md).

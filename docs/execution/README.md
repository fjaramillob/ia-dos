# Ejecución

Esta sección explica cómo IA-DOS transforma decisiones confirmadas en cambios verificables sobre artefactos reales.

## Documentos

- [Coding agents](coding-agents.md): rol, frontera con el Project Orchestrator, entrada mínima, conducta y evidencia esperada.
- [Actualizar la LLM Wiki](updating-the-llm-wiki.md): flujo completo desde el conocimiento confirmado hasta el pull request documental.
- [Preparar y revisar el handoff](../getting-started/execution-handoff.md): recorrido para delimitar y entregar una tarea.
- [Execution Task](../../templates/execution-task.template.md): plantilla general para definir objetivo, alcance, límites y pruebas.
- [Wiki Update Task](../../templates/wiki-update-task.template.md): plantilla especializada para crear o mantener memoria durable.
- [Execution Report](../../templates/execution-report.template.md): plantilla para devolver cambios y evidencia.
- [Prompt de handoff](../../prompts/execution/handoff-to-coding-agent.md): instrucción general para entregar una tarea a un agente.
- [Prompt para actualizar la wiki](../../prompts/execution/update-llm-wiki.md): instrucción específica para Codex, Antigravity, Claude Code u otro coding agent.

## Regla operativa

```text
1 Execution Task
→ 1 ejecución acotada
→ 1 resultado verificable
→ 1 Execution Report
```

Para la LLM Wiki:

```text
conocimiento confirmado
→ Wiki Update Task
→ coding agent
→ diff + validaciones + Execution Report
→ revisión
→ merge autorizado
```

La aprobación de una decisión no autoriza automáticamente la modificación de repositorios. La ejecución requiere alcance, acceso y autorización explícitos.
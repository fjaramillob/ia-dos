# Ejecución

Esta sección explica cómo IA-DOS transforma decisiones confirmadas en cambios verificables sobre artefactos reales.

## Documentos

- [Coding agents](coding-agents.md): rol, frontera con el Project Orchestrator, entrada mínima, conducta y evidencia esperada.
- [Preparar y revisar el handoff](../getting-started/execution-handoff.md): recorrido para delimitar y entregar una tarea.
- [Execution Task](../../templates/execution-task.template.md): plantilla para definir objetivo, alcance, límites y pruebas.
- [Execution Report](../../templates/execution-report.template.md): plantilla para devolver cambios y evidencia.
- [Prompt de handoff](../../prompts/execution/handoff-to-coding-agent.md): instrucción operativa para entregar una tarea a un agente.

## Regla operativa

```text
1 Execution Task
→ 1 ejecución acotada
→ 1 resultado verificable
→ 1 Execution Report
```

La aprobación de una decisión no autoriza automáticamente la modificación de repositorios. La ejecución requiere alcance, acceso y autorización explícitos.
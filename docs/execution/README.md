# Ejecución

Esta sección explica cómo IA-DOS transforma resultados confirmados en inspección, readiness o cambios verificables sobre artefactos reales.

## Camino de decisión

Antes de escribir:

```text
resultado verificable
→ Memory Bootstrap Gate cuando depende de historia chat-only
→ Environment Preflight cuando readiness indispensable es desconocido
→ Planning Task cuando falta inspección/diseño
→ Execution Task cuando la unidad está lista
→ Execution Cell o entorno autorizado
→ Execution Report
→ revisión del Cycle Owner
→ aprobación humana cuando corresponda
```

No es una pipeline rígida: cada gate se usa sólo cuando aplica.

## Documentos

- [Coding agents](coding-agents.md): roles Planning/Execution, límites y evidencia.
- [Execution Cells y Exchange](execution-cells-and-exchange.md): continuidad de ejecución y pasarela pasiva de `.md`.
- [Readiness y Execution Resume](environment-readiness-and-resume.md): precondiciones del entorno y reanudación segura.
- [Autoridad de fuentes y artefactos](source-and-artifact-authority.md): qué demuestra cada recurso y qué acceso se permite.
- [Actualizar la memoria durable](updating-the-llm-wiki.md): materialización autorizada de conocimiento confirmado.
- [Preparar y revisar el handoff](../getting-started/execution-handoff.md): recorrido completo de delegación.
- [Execution Task compacta](../../templates/execution-task-compact.template.md)
- [Execution Task completa](../../templates/execution-task.template.md)
- [Execution Resume](../../templates/execution-resume.template.md)
- [Execution Report](../../templates/execution-report.template.md)
- [Wiki Update Task](../../templates/wiki-update-task.template.md)
- [Prompt de handoff](../../prompts/execution/handoff-to-coding-agent.md)
- [Prompt para actualizar memoria](../../prompts/execution/update-llm-wiki.md)

## Regla operativa

```text
1 Execution Task
→ 1 ejecución acotada
→ 1 resultado verificable
→ 1 Execution Report
```

Una Execution Cell puede conservar continuidad entre múltiples tareas, pero cada tarea vuelve a declarar permisos.

El Execution Report es evidencia; no aprueba su propio resultado, no elige la siguiente unidad y no recomienda memoria durable por defecto.

## Memoria durable Markdown

Cuando el conocimiento ya está confirmado y la actualización documental está autorizada:

```text
conocimiento confirmado
→ Execution Task / perfil Wiki Update Task
→ Coding Agent — Execution
→ diff + validaciones + Execution Report
→ revisión
→ integración sólo cuando esté autorizada
```

`memoria durable` es la responsabilidad funcional; `LLM Wiki` es una posible materialización.

## Responsabilidad

La aprobación de una decisión no autoriza automáticamente modificar recursos.

El Cycle Owner gobierna dentro de autoridad delegada. La persona responsable conserva la aprobación final cuando cambian dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

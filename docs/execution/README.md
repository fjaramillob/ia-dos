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
- [Entrega manual de artefactos](manual-artifact-delivery.md): Manual Artifact Launcher, Output Delivery y Caveman Return.
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
- [Prompt de Planning](../../prompts/execution/handoff-to-planning-agent.md)
- [Manual Artifact Launcher](../../prompts/execution/manual-artifact-launcher.md)
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

## Exchange manual

Cuando un proyecto adopta Exchange de forma manual:

```text
artefacto completo en inbox
→ Manual Artifact Launcher
→ Code Agent
→ si la Task autoriza Output Delivery: artefacto completo en el destino declarado
→ si además declara Caveman Return: Sí y la materialización fue correcta: Caveman Return en conversación
```

Si la Task no autoriza `Output Delivery`, el mero uso de Exchange o del launcher no permite escribir en `outbox`. Si no declara `Caveman Return: Sí` o el output completo no fue materializado correctamente, se devuelve el artefacto completo según el contrato y canal de la Task.

El launcher sólo localiza archivos. `Output Delivery` autoriza únicamente la materialización declarada. El Caveman Return es una representación conversacional mínima y no reemplaza el Implementation Plan, Environment Readiness Report o Execution Report completo.

En una Planning Task o Preflight, escribir únicamente el artefacto de salida autorizado no convierte la inspección del proyecto en una operación de escritura.

## Identidad de Execution Task

El Conversation Agent asigna el Task ID al adoptar y construir una Execution Task real. Una candidata de Planning permanece:

```text
Task ID: PENDIENTE — ASIGNAR AL ADOPTAR
```

Cuando el proyecto no tiene otro esquema, IA-DOS recomienda:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

El esquema temporal no es una obligación universal para IDs de Planning.

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

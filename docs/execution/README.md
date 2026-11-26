# Ejecución

Esta sección explica cómo IA-DOS transforma resultados confirmados en inspección, readiness o cambios verificables sobre artefactos reales.

## Caminos de decisión

Antes de escribir, resuelve primero Method Resolution Policy y luego elige el entry mode de esta ejecución.

```text
ORCHESTRATED
outcome verificable
→ Memory Bootstrap Gate sólo si falta memoria durable indispensable
→ Planning / Preflight sólo cuando aportan
→ Execution Task outcome-first + Revalidate
→ planificar internamente / implementar / diagnosticar / reparar / safe retry
→ Execution Report
→ revisión del Cycle Owner

DIRECT
instrucción humana vigente
+ contratos durables
+ estado real
→ Effective Execution Contract
→ Direct Execution Gate
→ PASS: self-plan / execute / verify / maintain continuity
→ NEEDS_GOVERNANCE sólo ante decisión material
```

No es una pipeline rígida. En DIRECT no materialices Task/Report por ceremonia si el contrato efectivo y la evidencia conversacional son suficientes.

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

Cuando existe una Execution Task:

```text
1 Execution Task
→ 1 outcome cohesivo
→ 1 frontera estable
→ 1 Execution Report
```

En DIRECT sin Task física, el Effective Execution Contract ocupa esa función y la salida puede ser evidencia compacta. Una Execution Cell puede conservar continuidad entre múltiples outcomes, pero nunca acumula permisos.

El Execution Report es evidencia; no aprueba su propio resultado ni elige la siguiente unidad. Puede reportar `Durable Memory Impact` y `Operational Baseline` cuando la Task ya definió esa política.

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

La memoria semántica se gobierna con `Memory Policy: NONE | CONDITIONAL | REQUIRED` y `Memory Stewardship: LOCAL | 90_STRUCTURAL | NO APLICA`.

La memoria `LOCAL` y el Operational Baseline pueden materializarse dentro del mismo outcome, sea mediante Execution Task o Effective Execution Contract en DIRECT. Cuando el impacto durable es estructural y el proyecto adopta `90 — Documentación y memoria`, el executor reporta `ROUTE_TO_90` y el Cycle Owner deriva la síntesis mediante Specialist Handoff.

Una Task WIKI separada se reserva para bootstrap, consolidación, custodia estructural, reparación/migración o una frontera documental distinta.

Cuando cambia un baseline publicado en un proyecto con LLM Wiki, el mismo outcome debe mantener continuidad operacional durable aunque la memoria semántica sea `NONE`.

`memoria durable` es la responsabilidad funcional; `LLM Wiki` es una posible materialización.

## Responsabilidad

La aprobación de una decisión no autoriza automáticamente modificar recursos.

El Cycle Owner gobierna dentro de autoridad delegada. La persona responsable conserva la aprobación final cuando cambian dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

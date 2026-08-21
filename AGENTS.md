# AGENTS.md

Este archivo contiene instrucciones persistentes para agentes que modifican el repositorio de IA-DOS.

## Propósito

IA-DOS es un método de orquestación para proyectos asistidos por IA. El repositorio define contratos, documentación, templates, prompts y material de adopción; no es una aplicación de runtime.

Cuando modifiques el repositorio, prioriza coherencia metodológica, simplicidad operacional y trazabilidad. No conviertas una mejora documental acotada en un rediseño del framework.

## Regla de cambio mínimo

Antes de escribir:

1. identifica qué contrato o superficie necesita cambiar;
2. lee sólo las fuentes canónicas directamente relacionadas;
3. comprueba si el cambio afecta otras representaciones del mismo contrato;
4. modifica el mínimo conjunto coherente;
5. valida que no dejas una variante normativa anterior en otra superficie vigente.

No cambies archivos vecinos sólo para “modernizarlos” si no existe contradicción real.

## Orden de autoridad documental

Usa, según el tema:

1. archivos raíz y `ORCHESTRATOR.md` para identidad, onboarding y reglas operativas generales;
2. `docs/foundations/` para contratos fundacionales;
3. `docs/orchestration/` y `docs/execution/` para routing, artefactos, roles y ejecución;
4. `templates/` y `prompts/` como superficies copiables que deben permanecer alineadas con esos contratos;
5. `research/` como contexto e influencia, nunca como autoridad normativa por sí sola.

No leas toda la documentación por defecto. Amplía la lectura sólo cuando el cambio pueda afectar contratos transversales.

## Contratos que requieren revisión transversal

Si modificas alguno de estos conceptos, comprueba sus representaciones relacionadas antes de cerrar:

- responsabilidad humana, `Conversation Space` y `Cycle Owner`;
- `Planning Task` e `Implementation Plan`;
- `Environment Preflight` y `Execution Resume`;
- `Execution Task`;
- `Execution Cell`;
- `Execution Report`;
- `Memory Bootstrap Gate`;
- memoria durable / `LLM Wiki`;
- Exchange;
- tipado de artefactos;
- `Output Delivery`, `Manual Artifact Launcher` y `Caveman Return` cuando se adopten;
- Current Offline Pack.

Una modificación de un contrato canónico no debe dejar una variante incompatible en templates, onboarding, `ORCHESTRATOR.md` o distribución offline.

## Invariantes consolidados

Mantén estas fronteras salvo decisión explícita que las cambie:

```text
Persona responsable = dirección y aprobación final aplicable
Conversation Space   = gobierno dentro de autoridad delegada
Execution Cell       = continuidad de ejecución
Execution Task       = contrato de una unidad
Execution Report     = evidencia de ejecución
Memoria durable      = responsabilidad funcional
LLM Wiki             = materialización durable, portable y navegable
Repository           = implementación
Exchange             = pasarela pasiva de archivos
```

Además:

- `00 — Dirección y orquestación` es el Conversation Space inicial canónico;
- los Conversation Spaces se abren bajo demanda, no como fases obligatorias;
- `50` no es un dispatcher obligatorio;
- una tarea no implica una conversación nueva del coding agent;
- una Execution Cell puede reutilizarse entre tareas sin heredar permisos;
- la autorización de una Execution Task es explícita y no acumulativa;
- el `Task ID` lo asigna el Conversation Agent que construye la tarea;
- Exchange no define IDs, artefactos, filenames, templates, estados, permisos, backlog, memoria, decisiones o workflow;
- `Manual Artifact Launcher` es efímero y no autoritativo: sólo localiza input y, cuando aplica, destino físico del output;
- `Output Delivery` sólo autoriza materializar el artefacto de salida expresamente declarado; no amplía permisos sobre proyecto, entorno o recursos inspeccionados;
- `Caveman Return` sólo puede compactar la conversación cuando la Task lo declara y el output completo ya fue materializado; nunca sustituye el artefacto canónico;
- `Coding Agent — Planning` y `Environment Preflight` son de solo lectura respecto del proyecto/entorno, aunque puedan materializar su propio output cuando exista autorización explícita de `Output Delivery`;
- `Execution Report` no aprueba su propio resultado ni elige la decisión de gobierno posterior;
- el Cycle Owner revisa y gobierna dentro de la autoridad delegada; no sustituye la aprobación humana cuando una decisión cambia dirección, autoridad, riesgo o impacto reservado a la persona responsable;
- antes de emitir una Planning Task o Execution Task que dependa de historia previa, `Memory Bootstrap Gate` evalúa si existe conocimiento relevante únicamente en conversaciones efímeras y exige persistir el checkpoint mínimo cuando corresponda;
- después de revisar un Execution Report, el gobierno conversacional evalúa qué hechos nuevos merecen consolidarse en memoria durable; el coding agent no incorpora ni recomienda memoria adicional por defecto salvo que la propia tarea autorice una actualización documental concreta;
- el coding agent no lee una LLM Wiki completa por defecto;
- la política universal de persistencia o renovación de conversaciones de Planning permanece abierta.

## LLM Wiki y memoria durable

Usa los términos de forma consistente:

```text
memoria durable
= responsabilidad funcional de conservar conocimiento vigente y reutilizable

LLM Wiki
= materialización durable, portable y navegable de esa memoria
  para humanos y agentes
```

Una LLM Wiki:

- normalmente usa Markdown estándar y enlaces relativos;
- debe poder navegarse con herramientas como GitHub, editores u Obsidian sin depender de ellas para su semántica;
- no es obligatoria para toda tarea ni requiere un repositorio separado;
- no debe convertirse por defecto en backlog, archivo de TASK/REPORT, log de chats o transcripciones.

## Reglas para agentes

1. No agregues conceptos, herramientas, carpetas o procesos no solicitados ni justificados por una contradicción real.
2. No presentes como implementado algo que sólo está propuesto, decidido o pendiente.
3. Mantén el contenido principal en español.
4. Conserva nombres técnicos establecidos cuando corresponda, por ejemplo `README.md`, `AGENTS.md`, `issue`, `pull request`, `branch`, `commit`, `Conversation Space`, `Project Orchestrator`, `Execution Task`, `Execution Cell`, `Execution Report` y `LLM Wiki`.
5. Explica términos nuevos cuando no sean autoexplicativos en contexto.
6. Evita lenguaje promocional, promesas futuras y complejidad no validada.
7. Mantén IA-DOS independiente de una herramienta específica.
8. No introduzcas referencias a proyectos particulares en contratos genéricos salvo que estén claramente marcadas como ejemplos.
9. Distingue conversación, memoria, implementación, evidencia y transporte.
10. No trates conversaciones o Exchange como fuente de verdad durable.
11. No reintroduzcas `Context Packs` como requisito operativo vigente salvo decisión explícita.
12. No introduzcas CLI, agentes autónomos propios, watchers, polling, triggers, RAG automático, registries o automatización compleja durante la etapa alpha sin una decisión explícita de alcance.

## Estado actual

IA-DOS está en etapa **alpha de adopción en proyectos reales**.

Los fundamentos y la consolidación operacional ya fueron completados. El foco actual es validar los contratos mediante uso real antes de añadir nuevas abstracciones.

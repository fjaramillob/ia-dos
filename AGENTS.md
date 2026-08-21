# AGENTS.md

## Propósito

Este repositorio contiene **IA-DOS**, un framework abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, planificación técnica, ejecución acotada, memoria durable y verificación basada en evidencia.

Estas instrucciones gobiernan a los agentes que modifican **el repositorio IA-DOS**. No sustituyen los contratos operativos de los proyectos que adopten el método.

## Principio de trabajo

Haz el cambio mínimo que resuelva la necesidad planteada y mantén coherencia con los contratos canónicos.

No conviertas una tarea documental en una oportunidad para rediseñar IA-DOS completo.

## Fuentes y jerarquía

Antes de actuar, consulta sólo las fuentes necesarias para el alcance actual.

Prioridad general:

1. `AGENTS.md` para reglas de trabajo del repositorio.
2. El documento o template directamente afectado por la tarea.
3. Contratos canónicos relacionados cuando el cambio altere semántica compartida.
4. `README.md`, `ORCHESTRATOR.md`, `docs/index.md` o `ROADMAP.md` cuando el cambio afecte presentación, onboarding, operación o dirección del método.
5. `research/` como contexto e influencia, nunca como autoridad normativa por sí sola.

No leas toda la documentación por defecto. Amplía la lectura sólo cuando el cambio pueda afectar contratos transversales.

## Contratos que requieren revisión transversal

Si modificas alguno de estos conceptos, comprueba sus representaciones relacionadas antes de cerrar:

- `Conversation Space` y `Cycle Owner`;
- `Planning Task` e `Implementation Plan`;
- `Environment Preflight` y `Execution Resume`;
- `Execution Task`;
- `Execution Cell`;
- `Execution Report`;
- `Memory Bootstrap Gate`;
- memoria durable / `LLM Wiki`;
- Exchange;
- tipado de artefactos;
- Current Offline Pack.

Una modificación de un contrato canónico no debe dejar una variante incompatible en templates, onboarding, `ORCHESTRATOR.md` o distribución offline.

## Invariantes consolidados

Mantén estas fronteras salvo decisión explícita que las cambie:

```text
Conversation Space = gobierno y decisión
Execution Cell     = continuidad de ejecución
Execution Task     = contrato de una unidad
Execution Report   = evidencia de ejecución
LLM Wiki           = memoria durable materializada
Repository         = implementación
Exchange           = pasarela pasiva de archivos
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
- `Execution Report` no aprueba su propio resultado ni elige la decisión de gobierno posterior;
- la evaluación de memoria durable ocurre después de revisar evidencia, salvo que una tarea autorice explícitamente una actualización documental concreta;
- `Memory Bootstrap Gate` sólo bloquea cuando la siguiente unidad depende de conocimiento relevante que vive únicamente en conversaciones efímeras;
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

Consulta `ROADMAP.md` para el estado y horizonte vigentes.

## Criterios de calidad

Todo cambio debe:

- resolver una necesidad clara o una contradicción verificable;
- ser comprensible para personas que no sean programadoras expertas;
- evitar duplicar contratos sin necesidad;
- mantener terminología y enlaces consistentes;
- distinguir hechos, decisiones, propuestas, opciones y excepciones;
- preservar independencia de herramienta;
- considerar consumo de contexto y tokens;
- mantener equivalencia entre documentación canónica, templates, onboarding y distribución offline cuando comparten un contrato.

## Verificación mínima

Antes de cerrar una tarea:

- revisa el diff completo;
- confirma que el alcance declarado coincide con los archivos modificados;
- verifica enlaces relativos afectados;
- busca contradicciones con contratos relacionados;
- comprueba que no se reintroduzcan términos o modelos reemplazados;
- distingue claramente evidencia de ejecución y decisión de gobierno;
- reporta supuestos, limitaciones y pendientes reales.

Si una revisión automática detecta una contradicción válida, corrígela antes de considerar el trabajo listo.

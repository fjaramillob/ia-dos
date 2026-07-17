# Prompt de handoff hacia planificación técnica

Utiliza este prompt después de aprobar una `Planning Task`.

```text
Actúa como coding agent en modo de planificación técnica para una única Planning Task.

Esta Planning Task fue preparada por un Conversation Space especialista y debe volver al mismo Cycle Owner para revisión. No abras otra conversación ni respondas como Project Orchestrator.

Antes de comenzar:
1. Lee la Planning Task canónica completa.
2. Consulta solo las fuentes, artefactos y entornos autorizados.
3. Confirma quién preparó la tarea, quién la ejecuta, Cycle Owner, destino del Implementation Plan y espacio de escalamiento.
4. Confirma que el modo es solo lectura.
5. Declara cualquier limitación de acceso antes de inferir el estado.
6. Identifica las instrucciones propias de los recursos inspeccionados cuando estén autorizadas.

Durante la planificación:
- inspecciona el estado real;
- distingue hechos, inferencias y propuestas;
- respeta la autoridad de cada recurso;
- registra evidencia verificable para cada hallazgo que condicione la decisión: recurso, ruta o referencia, estado observado e interpretación;
- no modifiques artefactos;
- no crees commits, cambios remotos, despliegues o recursos externos;
- no amplíes el objetivo;
- mantén una sola incertidumbre técnica dominante;
- clasifica cada decisión pendiente como bloqueante, supuesto explícito, alternativa o decisión posterior;
- no detengas el plan por decisiones que puedan mantenerse de forma reversible y segura;
- propone una primera unidad pequeña, dependiente y verificable;
- prepara una Execution Task candidata lista para revisión cuando exista evidencia suficiente;
- menciona solo dependencias inmediatas; no diseñes detalladamente toda la iniciativa;
- detente cuando se active una condición de detención.

Al finalizar, entrega un `Implementation Plan` que incluya:
- fuentes y accesos utilizados;
- evidencia verificable de los hallazgos relevantes;
- estado actual comprobado;
- limitaciones y contradicciones;
- decisión recomendada;
- estrategia mínima;
- decisiones pendientes clasificadas;
- primera unidad recomendada;
- Execution Task candidata lista para copiar, cuando sea segura;
- una única razón bloqueante verificable cuando todavía no pueda prepararse;
- brechas de otro dominio, sin desarrollarlas;
- memoria o documentación futura;
- declaración de solo lectura.

Devuelve el plan directamente al Cycle Owner indicado.
No ejecutes la primera tarea ni prepares cambios físicos sin aprobación posterior del Cycle Owner.
No recomiendes abrir otra conversación antes de entregar la Execution Task candidata, salvo que exista una decisión humana indispensable que impida incluso diseñar una primera unidad segura.
```

## Instrucción visible para el usuario

El Conversation Space especialista debe entregar junto con la Planning Task una instrucción equivalente a:

> Abre Codex, Antigravity o el coding agent disponible sobre el entorno técnico autorizado. Pega la Planning Task completa en modo de planificación de solo lectura. Devuelve el Implementation Plan completo a este mismo Conversation Space para revisión.

No pidas abrir otro chat especialista para ejecutar la planificación.
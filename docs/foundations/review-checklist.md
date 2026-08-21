# Checklist de revisión del método

Usa esta lista para comprobar que un cambio no reintroduzca contratos superados ni mezcle responsabilidades.

## Identidad y alcance

- [ ] IA-DOS se entiende como framework operativo abierto para desarrollo de software asistido por IA.
- [ ] El propósito y público objetivo son comprensibles sin conocimientos avanzados.
- [ ] El método sigue siendo independiente de proveedor, modelo, editor, stack y topología física.
- [ ] No se prometen aplicaciones, agentes autónomos, CLI, watchers, RAG u automatizaciones inexistentes.

## Gobierno y responsabilidad

- [ ] `00 — Dirección y orquestación` es la entrada canónica y no un dispatcher obligatorio.
- [ ] Los Conversation Spaces se abren bajo demanda y no como fases.
- [ ] El Cycle Owner actúa dentro de autoridad delegada.
- [ ] La persona responsable conserva la aprobación final cuando cambian dirección, autoridad, riesgo o impacto relevante.
- [ ] El coding agent no aprueba su propio plan o ejecución ni inicia otra unidad automáticamente.

## Memoria

- [ ] Conversación y Exchange no se presentan como memoria durable.
- [ ] `memoria durable` y `LLM Wiki` se distinguen: responsabilidad funcional versus materialización.
- [ ] La LLM Wiki no se impone como repositorio separado ni como requisito para cada tarea.
- [ ] `Memory Bootstrap Gate` sólo bloquea cuando la siguiente unidad depende de conocimiento chat-only.
- [ ] El coding agent consume memoria selectivamente mediante contexto durable, referencias y lectura requerida.
- [ ] TASK/REPORT, logs, diffs y transcripciones no se convierten en Wiki por defecto.

## Planificación y ejecución

- [ ] Planning y Execution conservan roles y autorizaciones separadas.
- [ ] La política de conversaciones de Planning no se infiere desde Execution Cells.
- [ ] Readiness indispensable desconocido deriva a `Environment Preflight`.
- [ ] Sólo `LISTO PARA EJECUCIÓN` habilita aprobar o reanudar escritura.
- [ ] `Execution Resume` sólo aplica si objetivo, alcance, autoridad, seguridad y arquitectura permanecen sin cambios.
- [ ] Una `Execution Task` representa una sola unidad terminable y verificable.
- [ ] Una `Execution Cell` conserva continuidad, no especialidad ni permisos acumulados.
- [ ] Una conversación activa de Execution Cell se reutiliza mientras siga respondiendo bien.

## Retorno y evidencia

- [ ] El Execution Report usa `COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO`.
- [ ] `Atención requerida` describe un asunto concreto y no preselecciona una decisión de gobierno.
- [ ] El Execution Report es evidencia, no aprobación, backlog ni mecanismo de consolidación de memoria.
- [ ] La memoria posterior se evalúa después de revisar la evidencia, salvo actualización documental explícitamente autorizada en la propia tarea.

## Exchange

- [ ] Exchange se describe únicamente como pasarela pasiva y opcional de `.md`.
- [ ] No define artefactos, IDs, filenames, templates, estados, permisos, backlog, memoria, decisiones o workflow.
- [ ] `inbox/`, `outbox/` y `archive/` no se interpretan como máquina de estados.
- [ ] Los Task IDs son responsabilidad del Conversation Agent que construye la tarea.

## Coherencia del repositorio

- [ ] Los términos vigentes son consistentes entre README, ORCHESTRATOR, docs, prompts, templates y Current Offline Pack.
- [ ] `Launch Mode`, `Exchange Protocol v0` y `Context Pack` sólo aparecen como términos históricos o de compatibilidad, no como contratos vigentes.
- [ ] Los bundles históricos están marcados como históricos y no se reescriben como método actual.
- [ ] El Current Offline Pack refleja los contratos canónicos vigentes.
- [ ] No existen referencias a proyectos particulares salvo ejemplos claramente sintéticos.
- [ ] Enlaces relativos, rutas y nombres de archivos afectados son válidos.

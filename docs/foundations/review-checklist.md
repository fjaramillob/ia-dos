# Checklist de revisión del método

Usa esta lista para comprobar que un cambio no reintroduzca contratos superados ni mezcle responsabilidades.

## Identidad y alcance

- [ ] IA-DOS se entiende como framework operativo abierto para desarrollo de software asistido por IA.
- [ ] El propósito y público objetivo son comprensibles sin conocimientos avanzados.
- [ ] El método sigue siendo independiente de proveedor, modelo, editor, stack y topología física.
- [ ] No se prometen aplicaciones, agentes autónomos, CLI, watchers, RAG u automatizaciones inexistentes.

## Gobierno y responsabilidad

- [ ] `Method Resolution Policy` distingue `FOLLOW_CURRENT | PINNED`.
- [ ] Un SHA/versión mencionado sólo en chat, prompt o reporte no se interpreta como pin durable.
- [ ] `FOLLOW_CURRENT` se resuelve al comienzo del outcome y permanece estable durante esa ejecución.
- [ ] `Execution Entry Mode: ORCHESTRATED | DIRECT` aparece como caminos de primera clase.
- [ ] `Execution Entry Policy` se distingue del Mode y usa `ORCHESTRATED_DEFAULT | DIRECT_DEFAULT | FLEXIBLE`.
- [ ] `00 — Dirección y orquestación` es la entrada conversacional canónica, no gateway obligatorio de ejecución.
- [ ] Los Conversation Spaces se abren bajo demanda y no como fases.
- [ ] El Cycle Owner actúa dentro de autoridad delegada.
- [ ] La persona responsable conserva la aprobación final cuando cambian dirección, autoridad, riesgo o impacto relevante.
- [ ] El coding agent no aprueba su propio plan o ejecución ni inicia otra unidad automáticamente fuera de la instrucción humana vigente.
- [ ] En DIRECT, `Direct Execution Gate` exige outcome, invariantes, fronteras, autoridad, aceptación y memoria suficientes; si falta gobierno usa `NEEDS_GOVERNANCE`.

## Memoria

- [ ] Conversación y Exchange no se presentan como memoria durable.
- [ ] `memoria durable` y `LLM Wiki` se distinguen: responsabilidad funcional versus materialización.
- [ ] La LLM Wiki no se impone como repositorio separado ni como requisito para cada tarea.
- [ ] `Memory Bootstrap Gate` sólo bloquea cuando la siguiente unidad depende de conocimiento chat-only.
- [ ] El coding agent consume memoria selectivamente mediante contexto durable, referencias y lectura requerida.
- [ ] TASK/REPORT, logs, diffs y transcripciones no se convierten en Wiki por defecto.
- [ ] El contrato de ejecución aplicable declara o permite reconstruir `Memory Policy: NONE | CONDITIONAL | REQUIRED` cuando el proyecto usa memoria durable (`Execution Task` en ORCHESTRATED; `Effective Execution Contract` en DIRECT).
- [ ] Declara `Memory Stewardship: LOCAL | 90_STRUCTURAL | NO APLICA` cuando corresponda.
- [ ] `CONDITIONAL` depende de triggers explícitos definidos por gobierno y no delega dirección al Coding Agent.
- [ ] Impacto estructural pendiente usa `ROUTE_TO_90`; una Wiki Task ya gobernada por 90 que materializa correctamente termina `UPDATED`.
- [ ] `current-state` permanece como snapshot/índice compacto con estado vigente, outcomes activos, milestones/capabilities relevantes, blockers, próximos horizontes ya aceptados y Operational Baseline cuando aplique.
- [ ] `DEFERRED` acumulado no deja materialmente incompleta la superficie caliente de memoria.
- [ ] Un cambio de baseline publicado actualiza el `Operational Baseline` aunque la memoria semántica sea `NONE`.
- [ ] El Operational Baseline distingue último HEAD remoto verificado de commit/versión productiva cuando divergen.
- [ ] La Wiki permite que un Coding Agent nuevo se oriente con repo + memoria relevante + contrato de ejecución aplicable y luego revalide la realidad.
- [ ] Una Wiki Update Task separada se reserva para bootstrap, consolidación, reparación/migración o frontera distinta; no es ritual posterior a cada ejecución.

## Planificación y ejecución

- [ ] Planning separado se usa sólo cuando existe una decisión material todavía no resuelta antes de escribir.
- [ ] La política de conversaciones de Planning no se infiere desde Execution Cells.
- [ ] Environment Preflight separado se usa sólo cuando readiness debe conocerse antes de conceder autoridad sensible, cuando la capacidad es objeto de evaluación o requiere otro actor/entorno.
- [ ] Toda Execution Task usa Revalidate para estado volátil ordinario.
- [ ] Una Execution Task declara Protected Invariants, Adaptation Authority y Protected Boundaries.
- [ ] Con BOUNDED, debugging, repair-in-place y safe retry reversibles permanecen dentro de la misma ejecución.
- [ ] Execution Resume se reserva para bloqueo externo, interrupción real o Human Decision Checkpoint resuelto y conserva outcome, invariantes, fronteras, alcance, autoridad, seguridad y arquitectura.
- [ ] Crear/materializar/rutear/iniciar una Task no se trata como decisión humana por sí misma cuando la autoridad ya está delegada.
- [ ] Los Human Decision Checkpoints derivan sólo decisiones materiales y no microaprobaciones de orquestación.
- [ ] Una `Execution Task` representa una sola unidad terminable y verificable.
- [ ] Una `Execution Cell` conserva continuidad, no especialidad ni permisos acumulados.
- [ ] Una conversación activa de Execution Cell se reutiliza mientras siga respondiendo bien.

## Retorno y evidencia

- [ ] El Execution Report usa `COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO`.
- [ ] `Atención requerida` describe un asunto concreto y no preselecciona una decisión de gobierno.
- [ ] El Execution Report es evidencia, no aprobación ni backlog.
- [ ] Cuando la Task declara memoria, el Report refleja `Durable Memory Impact` y estado de `Operational Baseline` sin inventar dirección.
- [ ] La memoria LOCAL puede materializarse dentro de la misma Execution Task cuando comparte outcome y Authority Envelope.
- [ ] La memoria estructural se deriva a `90 — Documentación y memoria` cuando el proyecto adopta ese custodio.

## Workspace Governance

- [ ] Se distingue topología durable de superficie efímera de ejecución.
- [ ] No se imponen máximos arbitrarios de branches, worktrees, agentes o previews.
- [ ] Nuevos repositorios, servicios, datastores o componentes canónicos se tratan como posible decisión material.
- [ ] Recursos efímeros tienen lifecycle y cleanup seguro.
- [ ] `PROJECT.md`, cuando existe, es mapa del workspace y no backlog/Wiki paralela.

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
- [ ] Los prompts operativos cotidianos no fijan un SHA de IA-DOS salvo reproducción histórica deliberada o pin durable explícito.
- [ ] No existen referencias a proyectos particulares salvo ejemplos claramente sintéticos.
- [ ] Enlaces relativos, rutas y nombres de archivos afectados son válidos.

# AGENTS.md

## Propósito

Este repositorio contiene **IA-DOS**, un framework abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, planificación técnica, ejecución acotada, memoria durable y verificación basada en evidencia.

Estas instrucciones gobiernan a los agentes que modifican **el repositorio IA-DOS**.

## Principio de trabajo

Haz el cambio mínimo que resuelva la necesidad planteada y mantén coherencia con los contratos canónicos.

No conviertas una tarea documental en una oportunidad para rediseñar IA-DOS completo.

## Fuentes y jerarquía

Antes de actuar, consulta sólo las fuentes necesarias para el alcance actual.

Prioridad general:

1. `AGENTS.md` para reglas de trabajo del repositorio.
2. El documento o template directamente afectado.
3. Contratos canónicos relacionados cuando el cambio altere semántica compartida.
4. `README.md`, `ORCHESTRATOR.md`, `docs/index.md` o `ROADMAP.md` cuando afecte presentación, onboarding, operación o dirección.
5. `research/` como contexto e influencia, nunca como autoridad normativa por sí sola.

No leas toda la documentación por defecto. Amplía la lectura sólo cuando el cambio pueda afectar contratos transversales.

## Contratos que requieren revisión transversal

Si modificas alguno de estos conceptos, comprueba sus representaciones relacionadas antes de cerrar:

- responsabilidad humana, `Conversation Space` y `Cycle Owner`;
- `Specialist Handoff` y routing entre Conversation Spaces;
- `Planning Task` e `Implementation Plan`;
- granularidad de `Execution Task`;
- `Authority Envelope`;
- `Environment Preflight` y `Execution Resume`;
- `Execution Cell` y checkpoints operacionales;
- `Execution Report`;
- `Memory Bootstrap Gate`;
- memoria durable / `LLM Wiki`;
- Exchange;
- `Output Delivery`, `Manual Artifact Launcher` y `Caveman Return`;
- Current Offline Pack;
- instalación y actualización de la referencia local.

Una modificación de un contrato canónico no debe dejar una variante incompatible en templates, onboarding, `ORCHESTRATOR.md` o distribución offline.

No reescribas evidencia histórica sólo porque conserve wording antiguo. Distingue superficies normativas vigentes de evidencia fechada.

## Invariantes consolidados

```text
Persona responsable = dirección y aprobación final aplicable
Conversation Space   = gobierno dentro de autoridad delegada
Specialist Handoff   = transferencia inline y copiable entre Conversation Spaces
Execution Cell       = continuidad de ejecución
Execution Task       = outcome cohesivo bajo una frontera estable de autoridad
Authority Envelope   = permisos explícitos dentro de la Execution Task
Execution Checkpoint = continuidad operacional, no autoridad
Execution Report     = evidencia de lo ocurrido
Memoria durable      = responsabilidad funcional
LLM Wiki             = materialización durable, portable y navegable
Repository           = implementación
Exchange             = pasarela pasiva opcional hacia/desde Coding Agents
```

Además:

- `00 — Dirección y orquestación` es el Conversation Space inicial canónico y no un dispatcher obligatorio;
- los Conversation Spaces se abren bajo demanda;
- `Specialist Handoff` se entrega inline; no requiere `.md`, Exchange, path ni launcher;
- si un Space es nuevo, se retoma después de un cambio relevante de IA-DOS o muestra reglas obsoletas, consulta sólo los contratos vigentes necesarios sin reiniciar onboarding;
- una Task no implica una conversación nueva del coding agent;
- una Execution Cell puede reutilizarse entre Tasks sin heredar permisos;
- IA-DOS no maximiza cantidad de Tasks: maximiza el outcome seguro y verificable por Task;
- no dividas sólo por duración, archivos, comandos, implementación, tests, commit, push, deploy o smoke;
- divide o detén cuando cambie materialmente outcome, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno;
- una acción sensible no declarada en la Task no está autorizada;
- una acción explícitamente declarada, con gates cumplidos y frontera estable, no requiere otra ida y vuelta humana por rutina;
- el coding agent nunca aprueba su propio plan o ejecución;
- `Authority Envelope` y `<TASK-ID>-CHECKPOINT.md` no son Artifact Types;
- `Execution Resume = Task original + delta del bloqueo resuelto` y conserva Task ID mientras objetivo, scope, autoridad, seguridad y arquitectura no cambien;
- `Execution Report` es evidence-first y no vuelve a narrar la Task;
- `Manual Artifact Launcher` es efímero y no autoritativo;
- `Caveman Return` compacta sólo después de materialización completa autorizada;
- Exchange es opcional, provider-agnostic, filesystem-first y pasivo;
- Exchange no depende de Google Drive; Drive, OneDrive, Dropbox, Syncthing, NAS o carpeta local/manual son sólo mecanismos posibles de transporte;
- `inbox/` contiene artifacts operativamente activos destinados a Coding Agents;
- `outbox/` contiene outputs pendientes de consumo o aún requeridos por trabajo activo;
- `archive/` es cold storage operacional por trazabilidad;
- `folder ≠ workflow state` y `archive ≠ aprobado/completado/memoria durable/repositorio de documentos vivos`;
- Exchange no enruta Conversation Spaces, no define IDs, templates, permisos, backlog, memoria o workflow;
- una Task es suficientemente autocontenida cuando `Task + Required Reading` permiten ejecutarla sin conversaciones previas;
- distingue `Embedded Contract`, `Required Reading` y `Reference`;
- Planning sigue siendo de solo lectura y el plan sigue siendo propuesta;
- el Cycle Owner puede adoptar un Implementation Plan dentro de autoridad delegada; la persona interviene ante cambios materiales de dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

## LLM Wiki y memoria durable

Una LLM Wiki:

- normalmente usa Markdown estándar y enlaces relativos;
- debe poder navegarse con GitHub, editores u Obsidian sin depender de ellos para su semántica;
- no es obligatoria para toda tarea ni requiere repositorio separado;
- no debe convertirse por defecto en backlog, archivo de TASK/REPORT, log de chats o transcripciones.

## Reglas para agentes

1. No agregues conceptos, herramientas, carpetas o procesos no solicitados ni justificados por contradicción real.
2. No presentes como implementado algo sólo propuesto o pendiente.
3. Mantén el contenido principal en español.
4. Conserva nombres técnicos establecidos.
5. Evita lenguaje promocional y complejidad no validada.
6. Mantén IA-DOS independiente de herramientas y proveedores.
7. No introduzcas referencias a proyectos particulares en contratos genéricos salvo ejemplos explícitos.
8. Distingue conversación, memoria, implementación, evidencia y transporte.
9. No trates conversaciones o Exchange como fuente de verdad durable.
10. No reintroduzcas `Context Packs` como requisito vigente.
11. No introduzcas CLI, agentes autónomos propios, watchers, polling, triggers, RAG automático, registries o automatización compleja durante alpha sin decisión explícita.
12. Archify u otra visualización técnica puede evaluarse como capacidad opcional y Supporting Artifact; no la conviertas en dependencia del core ni Artifact Type sin una decisión explícita.

## Estado actual

IA-DOS está en etapa **alpha de adopción en proyectos reales**. El foco es validar contratos mediante uso real antes de añadir nuevas abstracciones.

## Verificación mínima

Antes de cerrar una tarea:

- revisa el diff completo;
- confirma que el alcance coincide con los archivos modificados;
- verifica enlaces relativos afectados;
- busca contradicciones con contratos relacionados;
- busca residuos normativos de heurísticas reemplazadas;
- distingue evidencia histórica de contratos vigentes;
- confirma que no se reintroduzcan aprobaciones rutinarias no exigidas por la frontera de autoridad;
- confirma que Exchange no se confunda con un proveedor de sincronización;
- reporta supuestos, limitaciones y pendientes reales.

Si una revisión detecta una contradicción válida, corrígela antes de considerar el trabajo listo.
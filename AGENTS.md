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
Protected Invariants = propiedades materiales que no cambian durante la adaptación
Adaptation Authority = autonomía técnica explícita dentro de la Execution Task
Protected Boundaries = fronteras materiales que requieren gates o autoridad explícita
Authority Envelope   = permisos explícitos dentro de la Execution Task
Execution Checkpoint = continuidad operacional, no autoridad
Execution Report     = evidencia de lo ocurrido
Memory Stewardship   = LOCAL | 90_STRUCTURAL | NO APLICA
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
- no dividas sólo por duración, archivos, comandos, implementación, debugging, reparación, safe retry, tests, commit, push, deploy o smoke;
- con `Adaptation Authority: BOUNDED`, diagnostica, repara implementation defects, ajusta pruebas, elige mecanismos técnicamente equivalentes y realiza safe retry cuando no hubo side effects materiales y permanecen estables outcome, Protected Invariants y Protected Boundaries;
- divide o detén cuando cambie materialmente outcome, Protected Invariants, Protected Boundaries, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno;
- una acción sensible no declarada en la Task no está autorizada;
- una acción explícitamente declarada, con gates cumplidos y frontera estable, no requiere otra ida y vuelta humana por rutina;
- la mecánica de crear, materializar, rutear o iniciar una Task dentro de autoridad delegada no es por sí misma una decisión humana; el Cycle Owner puede continuar sin microaprobaciones mientras no cambie una frontera material;
- una Task larga puede declarar Human Decision Checkpoints y continuar con el mismo Task ID mediante Execution Resume cuando la decisión humana activa una opción ya prevista;
- el coding agent nunca aprueba su propio plan o ejecución;
- `Authority Envelope` y `<TASK-ID>-CHECKPOINT.md` no son Artifact Types;
- `Execution Resume = Task original + delta del bloqueo externo o interrupción real resuelta`; conserva Task ID mientras outcome, Protected Invariants, Protected Boundaries, scope, autoridad, seguridad y arquitectura no cambien;
- repair-in-place y safe retry dentro de una Execution todavía abierta no requieren Execution Resume;
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
- la memoria durable debe permitir que un Coding Agent competente, sin conversaciones previas, pueda orientarse con `repositorio + Wiki relevante + Task vigente` y contribuir tras revalidar el estado real;
- `Memory Policy = NONE | CONDITIONAL | REQUIRED` gobierna actualización semántica dentro de una Execution Task y no es un Artifact Type;
- `Memory Stewardship = LOCAL | 90_STRUCTURAL | NO APLICA` separa memoria local de custodia estructural; tampoco es un Artifact Type ni convierte a `90` en dispatcher;
- ante impacto durable estructural todavía no custodiado, el Execution Report usa `Durable Memory Impact: ROUTE_TO_90`; una Wiki Update Task ya gobernada por `90` que materializa correctamente reporta `UPDATED`;
- cuando un proyecto con LLM Wiki cambia un baseline publicado, el mismo outcome debe dejar actualizado un `Operational Baseline` durable con repositorio, branch productiva, último HEAD remoto verificado, commit productivo, deployment o release equivalente, entorno/URL, estado y fecha de verificación;
- el `Operational Baseline` es un checkpoint de continuidad, no sustituye revalidar Git, runtime o producción antes de escribir;
- un historial de releases, cuando exista, registra baselines publicados significativos de forma compacta; Git y la plataforma de delivery conservan el detalle exhaustivo;
- Planning separado sigue siendo de solo lectura y el plan sigue siendo propuesta, pero sólo se usa cuando existe una decisión material no resuelta antes de escribir; el detalle de implementación se planifica internamente dentro de Execution;
- Environment Preflight separado se usa sólo cuando readiness debe conocerse antes de conceder autoridad sensible, cuando la capacidad misma es el objeto de evaluación o cuando la inspección requiere otro actor/entorno; la revalidación volátil ordinaria ocurre dentro de Execution;
- el Cycle Owner puede adoptar un Implementation Plan dentro de autoridad delegada; la persona interviene ante cambios materiales de dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

## LLM Wiki y memoria durable

Una LLM Wiki:

- normalmente usa Markdown estándar y enlaces relativos;
- debe poder navegarse con GitHub, editores u Obsidian sin depender de ellos para su semántica;
- no es obligatoria para toda tarea ni requiere repositorio separado;
- debe privilegiar conocimiento vigente y suficiente para rehidratar a agentes nuevos;
- separa memoria semántica de baseline operacional;
- no debe convertirse por defecto en backlog, archivo de TASK/REPORT, log de chats, diffs ni transcripciones;
- no se actualiza semánticamente por cada ejecución: usa `NONE | CONDITIONAL | REQUIRED`;
- cuando el proyecto adopta `90 — Documentación y memoria`, los cambios estructurales de arquitectura, datos/source of truth, seguridad/autoridad, contratos cross-domain, capacidades mayores, gobernanza o reorganización relevante se derivan a ese custodio;
- `current-state` debe funcionar como snapshot/índice operativo compacto y permitir reconstruir estado vigente, outcomes activos, milestones/capabilities relevantes, blockers, próximos horizontes ya aceptados y Operational Baseline cuando aplique;
- varios outcomes `DEFERRED` deben consolidarse cuando su efecto acumulado vuelve materialmente incompleta esa superficie caliente; no uses cantidad de Tasks como umbral;
- si cambió un estado publicado, actualiza siempre el baseline operacional adoptado por el proyecto antes de considerar completamente cerrado ese outcome, salvo imposibilidad reportada explícitamente.

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
- confirma que no se reintroduzcan Planning/Preflight/Resume rutinarios que C03 absorbió dentro de Execution;
- confirma que no se reintroduzcan aprobaciones rutinarias no exigidas por Protected Boundaries;
- confirma que no se trate la creación/routing de una Task como decisión humana por sí misma;
- confirma que Human Decision Checkpoints no se usen para microaprobaciones y que una pausa material pueda continuar por Resume cuando la frontera siga estable;
- confirma que `DEFERRED` acumulado no deje `current-state` materialmente desactualizado;
- confirma que Exchange no se confunda con un proveedor de sincronización;
- reporta supuestos, limitaciones y pendientes reales.

Si una revisión detecta una contradicción válida, corrígela antes de considerar el trabajo listo.
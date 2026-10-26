# IA-DOS

**Intelligence-Assisted Development Operating System**

IA-DOS es un framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, memoria durable, planificación técnica cuando hace falta, ejecución acotada y verificación basada en evidencia.

Su objetivo es mantener separados:

```text
responsabilidad humana
≠ gobierno conversacional
≠ inspección técnica
≠ ejecución
≠ evidencia
≠ memoria durable
```

## Modelo actual

```text
Persona responsable
→ define dirección y autoridad

Conversation Space / Cycle Owner
→ gobierna dentro de autoridad delegada

Memory Bootstrap Gate
→ evita depender de conocimiento chat-only

Environment Preflight
→ comprueba readiness indispensable cuando es desconocido

Planning Task
→ inspección y diseño en solo lectura cuando hace falta

Execution Task
→ outcome cohesivo bajo una frontera estable de autoridad

Protected Invariants
→ lo que no puede cambiar mientras el agente adapta el método

Adaptation Authority
→ autonomía técnica explícita dentro de la frontera autorizada

Execution Cell
→ continuidad de ejecución cuando el proyecto la adopta

Execution Report
→ evidencia de ejecución

Memory Policy
→ decide impacto semántico durable dentro del outcome

Memory Stewardship
→ LOCAL | 90_STRUCTURAL según la naturaleza del cambio durable

Operational Baseline
→ último estado publicado verificado para continuidad

LLM Wiki
→ materialización durable, portable y navegable de memoria cuando se adopta

Exchange
→ pasarela pasiva opcional de archivos .md entre Conversation Agent y Coding Agent

Repository
→ implementación real
```

`00 — Dirección y orquestación` es la entrada canónica y recibe reorientaciones o escalamiento real. No funciona como dispatcher obligatorio.

La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

## Flujo de avance

El Project Orchestrator identifica el siguiente resultado verificable y evalúa:

```text
1. ¿El outcome está definido y verificable?
2. ¿Cuáles son los Protected Invariants?
3. ¿Qué puede adaptar autónomamente el Coding Agent?
4. ¿Dónde están las Protected Boundaries?
5. ¿Existe una decisión material aún no resuelta?
6. ¿Falta memoria estructural indispensable o readiness que deba conocerse antes de autorizar una frontera sensible?
```

El default es `Execution Task` outcome-first con planificación interna y `Revalidate` al comienzo. Según el caso:

- conocimiento estructural indispensable sólo en chats → `Memory Bootstrap Gate`, con custodia de `90` cuando el proyecto adopta ese rol;
- readiness que debe conocerse antes de conceder autoridad sensible → `Environment Preflight`;
- decisión material de diseño todavía abierta → `Planning Task`;
- outcome definido → `Execution Task` con Protected Invariants + Authority Envelope + Adaptation Authority;
- falta decisión de otro dominio → `Specialist Handoff` inline y copiable;
- decisión humana indispensable → deriva sólo esa decisión;
- reorientación → escala a `00`.

No es una pipeline rígida. Planning y Preflight separados son excepcionales; debugging, reparación y revalidación ordinarios viven dentro de la ejecución cuando la autoridad lo permite.

## Tipos de artefacto

Cada bloque transferible declara su receptor y salida esperada:

- `Specialist Handoff` → Conversation Space;
- `Planning Task` → Coding Agent — Planning;
- `Environment Preflight` → Coding Agent — Planning;
- `Environment Readiness Report` → Cycle Owner;
- `Implementation Plan` → Cycle Owner;
- `Execution Task` → Coding Agent — Execution;
- `Execution Resume` → Coding Agent — Execution;
- `Execution Report` → Cycle Owner.

El transporte o almacenamiento no crea tipos adicionales.

La frontera de entrega es explícita:

```text
Conversation Space → Conversation Space
→ Specialist Handoff inline, autocontenido y copiable
→ la persona copia/pega el bloque en la conversación destino
→ no requiere `.md`, Exchange, path ni Manual Artifact Launcher

Conversation Space → Coding Agent
→ Planning Task | Environment Preflight | Execution Task | Execution Resume
→ chat o `.md`/Exchange según el contrato de entrega
```

Una copia documental de un `Specialist Handoff` puede existir sólo si se solicita explícitamente o una convención local separada la conserva como archivo. Esa copia no sustituye ni condiciona la transferencia conversacional.

Consulta [Tipado de artefactos y validación del receptor](docs/orchestration/typed-artifact-routing.md).

## Compresión de contexto por autoridad

IA-DOS evita reenviar toda la historia del proyecto.

```text
fuentes de autoridad
+ artefacto previo válido
+ contexto durable estrictamente necesario
+ delta actual
+ contrato operativo explícito
```

- la memoria durable conserva conocimiento estable;
- la implementación demuestra estado técnico;
- cada tarea transporta sólo el contexto necesario y el cambio activo;
- permisos, límites, criterios y condiciones de detención permanecen explícitos;
- cuando una fuente no es accesible, se incluye sólo el extracto indispensable.

Consulta [Compresión de contexto por autoridad](docs/orchestration/context-compression-by-authority.md).

## Memory Bootstrap Gate

Antes de una Planning Task o Execution Task que dependa de decisiones, estado o historia previa, pregunta:

> ¿La siguiente unidad puede ejecutarse correctamente sin depender de conocimiento relevante que exista sólo en conversaciones efímeras?

```text
PASS
→ la unidad evaluada puede continuar sin documentación adicional

BOOTSTRAP REQUIRED
→ la unidad evaluada queda bloqueada
→ materializa primero el checkpoint durable mínimo en una unidad separada
→ revisa su evidencia
→ reevalúa el gate de la unidad original
```

`BOOTSTRAP REQUIRED` no impide emitir la Execution Task mínima cuyo **único resultado** sea crear o actualizar ese checkpoint. Esa tarea debe declarar explícitamente que materializa el bootstrap y no puede mezclar la unidad original que busca desbloquear.

No uses cantidad de mensajes, tareas o antigüedad como umbral.

Consulta [Memory Bootstrap Gate](docs/foundations/memory-bootstrap-gate.md).

## Memoria durable y LLM Wiki

IA-DOS mantiene memoria durable para que el proyecto sobreviva al cambio de conversaciones y agentes.

```text
memoria durable
= responsabilidad funcional de conservar conocimiento reusable

LLM Wiki
= materialización durable, portable y navegable

Memory Policy
= NONE | CONDITIONAL | REQUIRED para memoria semántica

Operational Baseline
= último estado publicado verificado para continuidad
```

Prueba práctica:

```text
repositorio real
+ Wiki relevante
+ Task vigente
→ un Coding Agent nuevo puede ponerse al día
→ revalida el estado real
→ puede aportar
```

No toda ejecución merece modificar semánticamente la Wiki. `CONDITIONAL` responde sólo a triggers explícitos del Cycle Owner; varios outcomes menores pueden consolidarse más adelante.

La continuidad publicada sí se conserva: cuando cambia producción/release, el Operational Baseline registra repo/branch, último HEAD remoto verificado, commit/versión publicada, deployment/release, entorno y fecha según aplique. `Repository HEAD` y `Production Commit` pueden diferir.

Cuando el proyecto adopta `90 — Documentación y memoria`, los cambios durables **estructurales** se derivan a ese Conversation Space mediante Specialist Handoff: arquitectura, datos/source of truth, seguridad/autoridad, contratos cross-domain, capacidades mayores, gobernanza o reorganización relevante de la memoria. `90` custodia síntesis y ubicación; no se convierte en dispatcher ni recibe cada ejecución.

El Operational Baseline y memoria estrecha no estructural pueden seguir actualizándose dentro de la misma Execution Task. Una Wiki Update Task separada queda para bootstrap, consolidación, reparación/migración, custodia estructural o una frontera de autoridad distinta.

La LLM Wiki no es obligatoria para cada proyecto ni exige repositorio separado. `current-state` debe mantenerse como snapshot/índice operativo compacto, no como acumulación cronológica. La Wiki no guarda TASK/REPORT, logs, diffs o transcripciones por defecto y el Coding Agent no la lee completa por rutina.

Consulta [Memoria durable portable y Obsidian](docs/foundations/durable-memory-and-obsidian.md).

## Planificación técnica

El Coding Agent puede planificar internamente cómo alcanzar un outcome autorizado. Usa una Planning Task separada sólo cuando existe una **decisión material todavía no resuelta antes de escribir**:

```text
Planning Task
→ Coding Agent — Planning en solo lectura
→ Implementation Plan
→ revisión del Cycle Owner
→ aprobación humana cuando corresponda
```

Un bug de implementación, una elección entre runners equivalentes o debugging ordinario no justifican por sí solos Planning separado. El plan debe cerrar una sola decisión material dominante y no convertirse por defecto en auditoría completa, arquitectura final o roadmap integral.

IA-DOS mantiene abierta la política universal de persistencia o renovación de conversaciones de Planning. Un nombre `PLAN — ...` no obliga a abrir una conversación nueva por tarea.

## Environment Preflight

Toda Execution Task revalida al comienzo las precondiciones volátiles indispensables. Usa un `Environment Preflight` separado sólo cuando el readiness deba conocerse **antes de conceder autoridad sensible**, cuando la capacidad misma sea el objeto de evaluación o cuando la inspección requiera un actor/entorno distinto.

Es de solo lectura y produce:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

No dupliques un Preflight reciente dentro de la Execution Task salvo las comprobaciones volátiles realmente necesarias.

## Ejecución y Execution Cells

Cuando una unidad está definida y autorizada:

```text
Execution Task
→ Execution Cell activa o entorno disponible
→ Coding Agent — Execution
→ Execution Report
→ revisión del Cycle Owner
```

Una `Execution Cell` conserva continuidad de ejecución. No representa una tarea, una profesión ni un Conversation Space.

Mantén una sola conversación activa por célula mientras siga respondiendo bien. No la renueves por edad, mensajes o cantidad de tareas. Renueva únicamente ante degradación, contaminación de contexto o necesidad real de contexto limpio.

Reutilizar una conversación no reutiliza permisos: cada `Execution Task` vuelve a declarar autoridad completa.

Consulta [Execution Cells y Exchange](docs/execution/execution-cells-and-exchange.md).

## Un solo contrato de Execution Task

```text
Execution Task
= outcome + Protected Invariants
+ alcance + Authority Envelope + Adaptation Authority
+ Protected Boundaries
+ criterios + verificaciones + condiciones de detención
```

Puede representarse con la [Execution Task compacta](templates/execution-task-compact.template.md), la [Execution Task completa](templates/execution-task.template.md) o el perfil documental [Wiki Update Task](templates/wiki-update-task.template.md).

Una unidad ordinaria que dependa de memoria previa requiere `Memory Bootstrap Gate = PASS`. La excepción es la unidad acotada que materializa el checkpoint requerido por `BOOTSTRAP REQUIRED`; después de revisar su reporte se reevalúa el gate de la unidad original.

El mecanismo de transporte no cambia ese contrato.

## Execution Resume

`Execution Resume` reanuda la misma Execution Task después de una interrupción real, acción externa o bloqueo que el executor no podía resolver dentro de su autoridad, siempre que sigan sin cambios outcome, alcance, autoridad, seguridad, arquitectura y Protected Invariants.

Con `Adaptation Authority: BOUNDED`, una reparación técnica ordinaria sin side effects materiales se resuelve **dentro de la misma ejecución** y no exige Resume. Conserva Task ID y no amplía permisos.

## Execution Report

El Execution Report es **evidencia**, no una decisión del Cycle Owner.

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
Durable Memory Impact: NONE | UPDATED | DEFERRED | ROUTE_TO_90 | ATTENTION REQUIRED
Operational Baseline: UNCHANGED | UPDATED | NO APLICA | BLOQUEADO
```

Los dos últimos campos aplican cuando la Task incluye contrato de memoria. El Coding Agent no decide roadmap, prioridades ni la siguiente unidad; sólo materializa y reporta dentro de la Memory Policy, triggers y autoridad recibidos.

El Cycle Owner revisa el resultado y conserva gobierno sobre cierre, reparación, consolidación futura o cambio de dirección.

Si el reporte corresponde a una tarea de memory bootstrap, su revisión no habilita automáticamente la unidad original: primero se reevalúa su gate.

## Exchange

Exchange es una **pasarela pasiva y opcional de archivos Markdown para el intercambio con Coding Agents**.

```text
Conversation Agent
→ construye Task/Preflight/Resume y asigna Task ID cuando aplica
→ Exchange almacena / expone
→ Coding Agent consume y produce output tipado
→ Exchange almacena / expone
→ Conversation Agent / Cycle Owner revisa
```

Exchange **no enruta Conversation Spaces**. Un `Specialist Handoff` entre Conversation Spaces se entrega inline y copiable; no necesita `inbox/`, path ni `Manual Artifact Launcher`.

Exchange no define:

- IDs;
- filenames;
- templates;
- tipos de artefacto;
- estados;
- permisos;
- workflow;
- backlog;
- memoria durable;
- decisiones;
- routing conversacional.

Una topología posible es:

```text
proyecto-exch/
├── inbox/
├── outbox/
└── archive/
```

Estas carpetas son ubicaciones físicas, no estados del método. Nada ocurre automáticamente por mover un archivo.

Consulta [Crear o conectar Exchange](docs/getting-started/bootstrap-exchange.md).

## Empieza

1. Crea un Project, Gem, chat persistente o entorno equivalente.
2. Sigue [Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md).
3. Entrega una descripción breve y las fuentes disponibles.
4. Comienza en `00 — Dirección y orquestación`.
5. Abre otros Conversation Spaces sólo cuando una brecha requiera contexto persistente propio; transfiere mediante un `Specialist Handoff` inline y copiable.
6. Aplica los gates de memoria, readiness, Planning y Execution según corresponda.
7. Reutiliza Execution Cells cuando aporten continuidad.
8. Usa Exchange sólo cuando una pasarela de `.md` hacia/desde Coding Agents aporte valor real.

Si la plataforma no puede navegar el repositorio canónico, usa el [Current Offline Pack](bundles/ia-dos-current-offline-pack.md) cuando declare `Estado: VIGENTE` y un baseline canónico. No combines bundles históricos.

## Contratos principales

- [Project Orchestrator](ORCHESTRATOR.md)
- [Documentación](docs/index.md)
- [Propiedad del ciclo](docs/orchestration/cycle-ownership.md)
- [Tipado de artefactos](docs/orchestration/typed-artifact-routing.md)
- [Compresión de contexto](docs/orchestration/context-compression-by-authority.md)
- [Execution Cells y Exchange](docs/execution/execution-cells-and-exchange.md)
- [Ejecución adaptativa y fronteras protegidas](docs/execution/adaptive-execution.md)
- [Readiness y Resume](docs/execution/environment-readiness-and-resume.md)
- [Memory Bootstrap Gate](docs/foundations/memory-bootstrap-gate.md)
- [Memoria durable portable](docs/foundations/durable-memory-and-obsidian.md)
- [Custodia de memoria estructural](docs/foundations/memory-stewardship.md)
- [Autoridad de fuentes y artefactos](docs/execution/source-and-artifact-authority.md)

## Plantillas principales

- [Project Intake Brief](templates/project-intake-brief.template.md)
- [Specialist Handoff](templates/conversation-space-handoff.template.md)
- [Planning Task compacta](templates/planning-task-compact.template.md)
- [Planning Task completa](templates/planning-task.template.md)
- [Implementation Plan](templates/implementation-plan.template.md)
- [Environment Preflight](templates/environment-preflight.template.md)
- [Environment Readiness Report](templates/environment-readiness-report.template.md)
- [Execution Task compacta](templates/execution-task-compact.template.md)
- [Execution Task completa](templates/execution-task.template.md)
- [Execution Resume](templates/execution-resume.template.md)
- [Execution Report](templates/execution-report.template.md)
- [Wiki Update Task](templates/wiki-update-task.template.md)
- [Adoption Manifest](templates/adoption.template.yaml)
- [Wiki Starter](templates/wiki-starter/00-home.md)

## Estado

IA-DOS está en etapa **alpha de adopción en proyectos reales**. Consulta [ROADMAP.md](ROADMAP.md).

## Licencia

Apache License 2.0.
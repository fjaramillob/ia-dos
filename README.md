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
→ unidad autorizada y verificable

Execution Cell
→ continuidad de ejecución cuando el proyecto la adopta

Execution Report
→ evidencia de ejecución

LLM Wiki
→ materialización durable, portable y navegable de memoria cuando se adopta

Exchange
→ pasarela pasiva opcional de archivos .md

Repository
→ implementación real
```

`00 — Dirección y orquestación` es la entrada canónica y recibe reorientaciones o escalamiento real. No funciona como dispatcher obligatorio.

La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

## Flujo de avance

El Project Orchestrator identifica el siguiente resultado verificable y evalúa:

```text
1. ¿El resultado está suficientemente definido y acotado?
2. Si depende de historia, ¿el conocimiento necesario ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿corresponde Planning?
```

Según el caso:

- conocimiento necesario sólo en chats → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección o diseño → `Planning Task`;
- unidad definida + memoria suficiente + entorno listo → `Execution Task`;
- decisión humana indispensable → deriva sólo esa decisión;
- reorientación → escala a `00`.

No es una pipeline rígida. Cada gate se usa únicamente cuando corresponde.

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

IA-DOS mantiene dos términos complementarios:

```text
memoria durable
= responsabilidad funcional de conservar conocimiento reusable

LLM Wiki
= materialización durable, portable y navegable de esa memoria
  para humanos y agentes
```

Una LLM Wiki no es obligatoria para cada proyecto o tarea y no exige un repositorio separado.

Cuando se usa Markdown, el starter vigente es deliberadamente pequeño:

```text
00-home.md
project-brief.md
status/current-state.md
decisions/
sources/
AGENTS.md
```

No crea por defecto `tasks/`, `context-packs/`, `log.md`, `CORE` ni páginas vacías de arquitectura.

El coding agent no lee toda la Wiki por defecto. La tarea distingue `Contexto durable necesario`, `Referencias Wiki` y `Lectura requerida`.

Consulta [Memoria durable portable y Obsidian](docs/foundations/durable-memory-and-obsidian.md).

## Planificación técnica

Cuando falta inspección o diseño:

```text
Planning Task
→ Coding Agent — Planning en solo lectura
→ Implementation Plan
→ revisión del Cycle Owner
→ aprobación humana cuando corresponda
```

El plan debe cerrar una sola decisión técnica dominante y proponer una primera unidad segura. No debe convertirse por defecto en auditoría completa, arquitectura final o roadmap integral.

IA-DOS mantiene abierta la política universal de persistencia o renovación de conversaciones de Planning. Un nombre `PLAN — ...` no obliga a abrir una conversación nueva por tarea.

## Environment Preflight

Cuando una futura Execution Task depende de runtime, herramienta, servicio, acceso, secreto o conectividad indispensable no comprobados, usa `Environment Preflight`.

Es de solo lectura y produce:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

Sólo `LISTO PARA EJECUCIÓN` permite aprobar o reanudar escritura.

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
= objetivo + alcance + autoridad + permisos
+ criterios + verificaciones + condiciones de detención
```

Puede representarse con la [Execution Task compacta](templates/execution-task-compact.template.md), la [Execution Task completa](templates/execution-task.template.md) o el perfil documental [Wiki Update Task](templates/wiki-update-task.template.md).

Una unidad ordinaria que dependa de memoria previa requiere `Memory Bootstrap Gate = PASS`. La excepción es la unidad acotada que materializa el checkpoint requerido por `BOOTSTRAP REQUIRED`; después de revisar su reporte se reevalúa el gate de la unidad original.

El mecanismo de transporte no cambia ese contrato.

## Execution Resume

`Execution Resume` reanuda la misma Execution Task después de resolver un bloqueo únicamente si siguen sin cambios:

- objetivo;
- alcance;
- autoridad;
- seguridad;
- arquitectura.

Conserva Task ID y no amplía permisos.

## Execution Report

El Execution Report es **evidencia**, no una decisión del Cycle Owner y no un artefacto de consolidación de memoria.

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El coding agent:

- no aprueba su propio resultado;
- no selecciona `APROBAR`, `CORREGIR`, `REVERTIR`, `ESCALAR` o `REVISAR MEMORIA`;
- no crea por defecto una sección de conocimiento potencialmente durable;
- no recomienda automáticamente una actualización de Wiki;
- no inicia la siguiente unidad.

Después de revisar la evidencia, el Cycle Owner actúa dentro de la autoridad delegada y la persona responsable interviene cuando corresponde. Separadamente se evalúa si hechos nuevos merecen memoria durable.

Si el reporte corresponde a una tarea de memory bootstrap, su revisión no habilita automáticamente la unidad original: primero se reevalúa su gate.

## Exchange

Exchange es una **pasarela pasiva y opcional de archivos Markdown**.

```text
Conversation Agent
→ construye artefacto y asigna Task ID cuando aplica
→ Exchange almacena / expone
→ Code Agent consume y produce retorno
→ Exchange almacena / expone
→ Conversation Agent / Cycle Owner revisa
```

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
- decisiones.

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
5. Abre otros Conversation Spaces sólo cuando una brecha requiera contexto persistente propio.
6. Aplica los gates de memoria, readiness, Planning y Execution según corresponda.
7. Reutiliza Execution Cells cuando aporten continuidad.
8. Usa Exchange sólo cuando una pasarela de `.md` aporte valor real.

Si la plataforma no puede navegar el repositorio canónico, usa el [Current Offline Pack](bundles/ia-dos-current-offline-pack.md) cuando declare `Estado: VIGENTE` y un baseline canónico. No combines bundles históricos.

## Contratos principales

- [Project Orchestrator](ORCHESTRATOR.md)
- [Documentación](docs/index.md)
- [Propiedad del ciclo](docs/orchestration/cycle-ownership.md)
- [Tipado de artefactos](docs/orchestration/typed-artifact-routing.md)
- [Compresión de contexto](docs/orchestration/context-compression-by-authority.md)
- [Execution Cells y Exchange](docs/execution/execution-cells-and-exchange.md)
- [Readiness y Resume](docs/execution/environment-readiness-and-resume.md)
- [Memory Bootstrap Gate](docs/foundations/memory-bootstrap-gate.md)
- [Memoria durable portable](docs/foundations/durable-memory-and-obsidian.md)
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
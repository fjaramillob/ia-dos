# Actualización de la memoria durable

Cuando el proyecto utiliza una Wiki Markdown, su contenido se gobierna desde el Project Orchestrator y, cuando aporta, desde `90 — Wiki y memoria`. La modificación física corresponde a un coding agent o a otro mecanismo autorizado con acceso real al recurso.

La Wiki conserva conocimiento vigente y reusable. No es un backlog, un log operacional ni un repositorio de TASK/REPORT.

## Separación de responsabilidades

```text
Project Orchestrator / Cycle Owner
    identifica conocimiento durable
    distingue estado, decisiones y desconocidos
    define qué debe cambiar y por qué
    prepara una Execution Task documental

90 — Wiki y memoria, cuando aporta
    sintetiza conocimiento
    detecta contradicciones y obsolescencia
    propone contenido y rutas
    no afirma cambios sin evidencia

Coding agent
    inspecciona la Wiki real
    modifica sólo rutas autorizadas
    mantiene Markdown portable
    revisa enlaces y diff
    entrega Execution Report
```

## Cuándo crear una actualización documental

Créala cuando:

- una decisión confirmada debe persistirse;
- cambia el estado real del proyecto;
- una implementación invalida información vigente;
- una restricción o arquitectura confirmada cambia;
- aparece una contradicción que debe resolverse en la memoria;
- el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md) devuelve `BOOTSTRAP REQUIRED`;
- la estructura actual dificulta recuperar selectivamente conocimiento que ya existe.

No es necesaria para cada conversación, commit menor o ajuste editorial sin impacto durable.

## Contrato de ejecución

Una actualización física de la Wiki sigue siendo una `Execution Task` canónica.

Puede utilizar el perfil [Wiki Update Task](../../templates/wiki-update-task.template.md), pero ese perfil no crea un tipo de artefacto independiente ni debilita alcance, autoridad, permisos, criterios, verificaciones o condiciones de detención.

## Entrada mínima para el coding agent

La tarea debe incluir:

- objetivo documental;
- conocimiento confirmado que debe reflejarse;
- fuentes o evidencia autorizadas;
- páginas que deben leerse;
- rutas modificables y prohibidas;
- contenido que debe preservarse;
- alcance y fuera de alcance;
- autorizaciones de branch, commit, push o PR;
- criterios de aceptación;
- validaciones requeridas;
- condiciones de detención;
- destino del Execution Report.

No envíes toda la historia del proyecto si la actualización necesita sólo unas pocas páginas y hechos vigentes.

## Conducta del coding agent

El coding agent debe:

1. confirmar recurso, branch o modo de trabajo y rutas autorizadas;
2. leer `AGENTS.md`, `.ia-dos.yaml` cuando exista, `00-home.md` o el home equivalente y sólo las páginas requeridas;
3. inspeccionar antes de modificar;
4. preservar información vigente fuera del alcance;
5. no inventar decisiones ni completar vacíos por simetría;
6. no convertir propuestas en hechos ni decisiones aceptadas en implementación;
7. mantener enlaces Markdown relativos y navegación coherente;
8. no introducir dependencia de Obsidian, plugins o wikilinks para semántica crítica;
9. ejecutar las validaciones aplicables;
10. revisar el diff completo;
11. devolver un Execution Report.

Una Wiki existente puede usar nombres de archivos distintos del starter. La tarea debe declarar las rutas reales; no renombres archivos sólo para normalizar nombres.

## Validaciones mínimas

Según la estructura de cada proyecto, verifica:

- Markdown legible;
- enlaces relativos afectados sin roturas conocidas;
- YAML válido cuando exista;
- rutas y nombres coherentes;
- navegación desde el home vigente;
- ausencia de secretos o datos no permitidos;
- separación explícita entre implementado, decidido/no implementado, pendiente y desconocido;
- ausencia de duplicación innecesaria;
- preservación del contenido fuera de alcance;
- diff limitado a rutas autorizadas.

Cuando exista tooling de validación, la tarea debe indicar los comandos exactos. Cuando no exista, realiza una revisión manual reproducible y repórtala.

## Git y pull request

Branch, commit, push, pull request y merge son capacidades separadas y deben estar autorizizadas explícitamente por la tarea.

No asumas que una actualización documental puede fusionarse automáticamente por ser de bajo riesgo.

## Revisión

El Cycle Owner y la persona responsable deben revisar:

- si el contenido corresponde a decisiones o evidencia reales;
- si el estado técnico está respaldado;
- si hipótesis y desconocidos siguen identificados;
- si se modificaron únicamente las rutas autorizadas;
- si el diff preserva conocimiento vigente;
- si las validaciones son suficientes;
- si aparece conocimiento nuevo que requiera otra decisión.

Una afirmación del coding agent no reemplaza la revisión del artefacto.

## Regla principal

```text
Conversation Space gobierna el conocimiento
Coding agent materializa cuando está autorizado
Wiki conserva estado durable
Execution Report aporta evidencia del cambio
```

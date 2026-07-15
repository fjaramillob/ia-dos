# Actualización de la LLM Wiki

La LLM Wiki es una fuente de verdad contextual. Su contenido se gobierna desde el Project Orchestrator y, cuando existe `90 — Wiki y memoria`, desde ese Conversation Space especializado. Su implementación física corresponde a un coding agent con acceso real al repositorio.

## Separación de responsabilidades

```text
Project Orchestrator
    comprende el conocimiento que debe registrarse
    distingue hechos, decisiones, hipótesis y preguntas abiertas
    define qué debe cambiar y por qué
    prepara una Wiki Update Task

90 — Wiki y memoria
    sintetiza conocimiento durable
    detecta contradicciones y obsolescencia
    propone páginas y contenido a actualizar
    no modifica por sí solo el repositorio

Coding agent
    inspecciona la wiki existente
    crea o modifica archivos autorizados
    valida estructura, enlaces y formatos
    revisa el diff
    entrega evidencia y Execution Report
```

`90` no es el agente que construye la wiki. Es el espacio conversacional que gobierna y sintetiza su contenido cuando ese trabajo requiere una conversación dedicada.

## Flujo operativo

```text
Conversación, hito o evidencia nueva
        ↓
Project Orchestrator o 90 identifica conocimiento durable
        ↓
clasifica hechos, decisiones, hipótesis y contradicciones
        ↓
Project Orchestrator prepara una Wiki Update Task
        ↓
coding agent inspecciona y materializa el cambio
        ↓
validaciones + diff + Execution Report
        ↓
revisión humana y del Project Orchestrator
        ↓
merge autorizado
        ↓
wiki actualizada como memoria durable
```

## Cuándo crear una Wiki Update Task

Créala cuando:

- una decisión confirmada debe registrarse;
- cambia el estado real del proyecto;
- una implementación invalida información anterior;
- cambia la arquitectura vigente;
- aparece una contradicción entre fuentes;
- debe crearse o actualizarse un Context Pack;
- la wiki inicial necesita materializarse;
- una página requiere reorganización que afectará varias rutas;
- el conocimiento durable existe solo en conversaciones o reportes.

No es necesaria para cada conversación, commit menor o ajuste editorial sin impacto durable.

## Entrada mínima para el coding agent

La Wiki Update Task debe incluir:

- objetivo documental;
- fuente del conocimiento;
- clasificación del contenido;
- repositorio y branch de trabajo;
- páginas autorizadas;
- páginas o contenido que deben preservarse;
- decisiones confirmadas;
- hipótesis que no deben convertirse en hechos;
- contradicciones conocidas;
- alcance y fuera de alcance;
- criterios de aceptación;
- validaciones requeridas;
- condiciones de detención;
- formato del Execution Report.

El Project Orchestrator debe entregar contexto suficiente, no toda la historia del proyecto.

## Conducta del coding agent

El coding agent debe:

1. confirmar repositorio, branch y rutas autorizadas;
2. leer `AGENTS.md`, `.ia-dos.yaml`, `index.md` y las páginas relevantes;
3. inspeccionar antes de modificar;
4. preservar información vigente fuera del alcance;
5. no inventar decisiones ni completar vacíos por simetría;
6. no convertir propuestas o hipótesis en estado implementado;
7. mantener enlaces y navegación coherentes;
8. actualizar `log.md` cuando las reglas de la wiki lo exijan;
9. ejecutar las validaciones aplicables;
10. revisar el diff completo;
11. entregar un Execution Report.

## Validaciones mínimas

Según la estructura de cada proyecto, verifica:

- Markdown legible y sin enlaces rotos conocidos;
- YAML válido en `.ia-dos.yaml` y front matter;
- rutas y nombres coherentes;
- navegación desde `index.md` cuando corresponda;
- ausencia de secretos o datos no permitidos;
- distinción explícita entre implementado, planificado y desconocido;
- ausencia de duplicación innecesaria de fuentes de verdad;
- preservación del contenido fuera de alcance;
- diff limitado a las rutas autorizadas.

Cuando exista tooling de validación, la tarea debe indicar los comandos exactos. Cuando no exista, el agente debe realizar una revisión manual reproducible y reportarla.

## Git y pull request

Por defecto, una actualización significativa de la wiki debe:

- realizarse en una branch dedicada;
- producir commits intencionales;
- abrir un pull request revisable;
- incluir resumen, fuentes, rutas modificadas y validaciones;
- no fusionarse sin autorización explícita.

Los cambios pequeños y reversibles pueden utilizar un flujo más ligero cuando el proyecto lo autorice, pero siempre deben conservar trazabilidad y evidencia.

## Revisión

El Project Orchestrator y la persona responsable deben revisar:

- si el contenido corresponde a decisiones o evidencia reales;
- si las hipótesis siguen identificadas como tales;
- si se modificaron únicamente las páginas autorizadas;
- si el diff preserva conocimiento vigente;
- si las validaciones son suficientes;
- si el cambio puede fusionarse.

Una afirmación del coding agent no reemplaza la revisión del artefacto.

## Regla principal

```text
El Project Orchestrator y 90 gobiernan el conocimiento.
El coding agent materializa la LLM Wiki.
Git y el pull request trazan el cambio.
La persona responsable autoriza el cierre.
```

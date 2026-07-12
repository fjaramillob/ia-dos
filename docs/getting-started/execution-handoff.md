# Handoff entre Project Orchestrator y coding agent

Este flujo convierte una necesidad de desarrollo en una tarea acotada, verificable y trazable.

No consiste en reenviar todo el historial del proyecto ni en pedir al agente que “resuelva lo necesario”.

## Flujo

```text
Necesidad o decisión
→ Execution Task aprobada
→ handoff con contexto mínimo
→ implementación y pruebas
→ Execution Report
→ revisión de evidencia
→ actualización de tarea, código y memoria durable
```

## Entradas mínimas

Antes de delegar, el Project Orchestrator debe contar con:

- objetivo confirmado;
- una fuente canónica para la tarea;
- `CORE` actualizado;
- uno o dos `Context Packs` relevantes;
- rutas reales del repositorio y la wiki;
- estado actual comprobado;
- guardrails y condiciones de detención;
- aprobación humana del alcance.

## Paquete de handoff

Entrega únicamente:

```text
CORE
+ Context Pack principal
+ Context Pack secundario, solo si es necesario
+ Execution Task canónica
+ AGENTS.md del repositorio
```

No adjuntes toda la wiki, todas las conversaciones, IA-DOS completo ni otros proyectos del workspace.

## 1. Preparar la Execution Task

Usa `templates/execution-task.template.md`.

La tarea debe definir:

- objetivo concreto;
- problema o evidencia;
- alcance y fuera de alcance;
- repositorios, rama y rutas autorizadas;
- criterios de aceptación observables;
- pruebas y evidencia esperadas;
- condiciones de detención;
- documentación o memoria que podría cambiar;
- formato de entrega.

La tarea debe vivir en un único lugar: GitHub Issue, archivo Markdown en la wiki o sistema equivalente declarado en `.ia-dos.yaml`.

No delegues una tarea que todavía dependa de una decisión importante sin resolver. Divide una tarea cuando mezcle objetivos independientes o varios subsistemas.

## 2. Revisar antes de delegar

Confirma:

- que el objetivo puede terminarse;
- que el alcance es pequeño y explícito;
- que las rutas permitidas y prohibidas son correctas;
- que el fuera de alcance protege comportamiento no relacionado;
- que no se autoriza producción, costes o recursos externos por omisión;
- que cada criterio de aceptación puede comprobarse;
- que las pruebas son aplicables;
- que el agente recibe solo el contexto necesario.

## 3. Ejecutar con el coding agent

El agente debe:

1. leer `AGENTS.md` y la `Execution Task` completa;
2. consultar solo el contexto indicado;
3. ejecutar `git status` antes de escribir;
4. inspeccionar el estado real;
5. modificar únicamente rutas autorizadas;
6. detenerse ante contradicciones o riesgos definidos;
7. ejecutar las pruebas aplicables;
8. revisar el diff completo;
9. devolver un `Execution Report`.

Puede utilizarse el prompt de `prompts/execution/handoff-to-coding-agent.md`.

## 4. Revisar el Execution Report

Usa `templates/execution-report.template.md`.

Compara:

- objetivo versus resultado;
- criterios de aceptación versus evidencia;
- alcance versus diff;
- pruebas solicitadas versus pruebas ejecutadas;
- fuera de alcance versus cambios reales;
- estado declarado versus estado Git;
- riesgos, limitaciones y decisiones pendientes.

Una afirmación del agente no sustituye evidencia. El estado `Completada` solo corresponde cuando los criterios aplicables tienen respaldo suficiente.

## 5. Cerrar el ciclo

Después de aprobar el resultado:

- actualiza la tarea en su fuente canónica;
- conserva la implementación en el repositorio de aplicación;
- conserva la evidencia en el pull request o reporte;
- registra decisiones durables en la wiki o ADR;
- actualiza `current-state.md` cuando cambie el estado real;
- actualiza `architecture.md` solo si cambió la arquitectura;
- actualiza `CORE` solo cuando cambie información transversal;
- registra en `log.md` el aprendizaje durable, no logs efímeros completos.

## Rechaza el cierre cuando

- faltan pruebas exigidas sin explicación;
- los criterios no tienen evidencia;
- aparecen cambios fuera de alcance;
- el reporte no coincide con el diff o el estado Git;
- se ocultaron fallos o trabajo incompleto;
- se tomaron decisiones no autorizadas;
- la documentación presenta propuestas como implementadas.

## Verificación final

- [ ] Existe una sola fuente canónica.
- [ ] El objetivo es único y terminable.
- [ ] El contexto es mínimo y suficiente.
- [ ] Alcance, fuera de alcance y rutas están explícitos.
- [ ] Los criterios de aceptación y pruebas son verificables.
- [ ] Las condiciones de detención están presentes.
- [ ] El agente debe devolver un reporte estructurado.
- [ ] El cierre exige evidencia y revisión humana.
- [ ] La memoria durable tiene un destino definido.

Valida este flujo primero con una tarea de bajo riesgo.
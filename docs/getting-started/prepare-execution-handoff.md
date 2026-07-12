# Preparar el handoff hacia un coding agent

El handoff convierte una necesidad conversacional en una tarea de desarrollo acotada, verificable y trazable.

No debe consistir en reenviar todo el historial del proyecto ni en pedir al agente que “resuelva lo necesario”.

## Entradas mínimas

Antes de preparar una `Execution Task`, el Project Orchestrator debe contar con:

- objetivo confirmado;
- fuente canónica de la tarea;
- `CORE` actualizado;
- uno o dos `Context Packs` relevantes;
- rutas reales de app y wiki;
- estado actual comprobado;
- restricciones y guardrails;
- criterio humano de aprobación.

## Estructura del handoff

El paquete mínimo contiene:

```text
CORE
+ Context Pack principal
+ Context Pack secundario opcional
+ Execution Task
+ AGENTS.md de la app
```

No entregues el repositorio IA-DOS completo para cada tarea cotidiana.

## Paso 1 — Definir una sola fuente canónica

La tarea debe vivir en un único lugar:

- GitHub Issue; o
- archivo Markdown en la wiki; o
- sistema equivalente declarado en `.ia-dos.yaml`.

No mantengas copias completas divergentes en chat, issue y wiki.

## Paso 2 — Completar la Execution Task

Utiliza `templates/execution-task.template.md`.

La tarea debe incluir:

1. objetivo concreto;
2. contexto mínimo;
3. problema y evidencia;
4. alcance incluido;
5. fuera de alcance;
6. repositorios y rutas autorizadas;
7. guardrails;
8. criterios de aceptación;
9. pruebas;
10. condiciones de detención;
11. documentación o memoria que podría requerir actualización;
12. formato de entrega.

## Paso 3 — Revisar el alcance

Antes de enviar la tarea, confirma:

- que no mezcla objetivos independientes;
- que no exige una decisión todavía no tomada;
- que no abre acceso innecesario a otros proyectos;
- que no autoriza cambios en producción por omisión;
- que las rutas permitidas y prohibidas son explícitas;
- que el fuera de alcance es visible;
- que cada criterio de aceptación es comprobable.

Cuando una tarea requiera varias decisiones o subsistemas, divídela.

## Paso 4 — Preparar el prompt operativo

El prompt al coding agent debe:

- indicar que lea `AGENTS.md`;
- señalar la fuente canónica de la tarea;
- entregar solo las rutas de contexto necesarias;
- exigir inspección y `git status` antes de escribir;
- recordar condiciones de detención;
- exigir un `Execution Report` al finalizar.

## Paso 5 — Ejecutar y conservar evidencia

Durante la ejecución, el agente debe:

- trabajar en la rama autorizada;
- limitarse a las rutas permitidas;
- ejecutar pruebas aplicables;
- conservar evidencia suficiente;
- detenerse cuando se active una condición definida;
- reportar trabajo incompleto sin ocultarlo.

## Paso 6 — Revisar el Execution Report

Utiliza `templates/execution-report.template.md`.

El Project Orchestrator o responsable humano debe comparar:

- objetivo versus resultado;
- criterios de aceptación versus evidencia;
- alcance versus diff;
- pruebas solicitadas versus pruebas ejecutadas;
- fuera de alcance versus cambios reales;
- riesgos reportados versus impacto;
- estado declarado versus estado Git.

Un agente no cierra una tarea por afirmar que está lista.

## Paso 7 — Cerrar el ciclo de memoria

Después de aprobar el resultado, identifica qué información durable debe volver a:

- `current-state.md`;
- `architecture.md`;
- `decisions/`;
- `log.md`;
- fuentes o Context Packs;
- issue o tarea canónica;
- pull request.

No copies logs efímeros completos a la wiki. Conserva decisiones, estado y aprendizaje durable.

## Estados posibles

- `Completada`: todos los criterios tienen evidencia suficiente.
- `Parcial`: existe avance útil, pero faltan criterios.
- `Bloqueada`: una condición de detención impide continuar.
- `Cancelada`: el trabajo dejó de ser necesario o autorizado.

## Verificación final

- [ ] Existe una sola fuente canónica.
- [ ] La tarea tiene objetivo único.
- [ ] El contexto es mínimo y suficiente.
- [ ] Alcance y fuera de alcance están explícitos.
- [ ] Las rutas autorizadas son concretas.
- [ ] Los criterios de aceptación son verificables.
- [ ] Las pruebas están definidas.
- [ ] Las condiciones de detención están presentes.
- [ ] El agente debe entregar un reporte estructurado.
- [ ] El cierre exige evidencia y revisión humana.
- [ ] La memoria durable tiene un destino definido.

## Siguiente paso

Ejecuta una tarea de bajo riesgo para validar el flujo completo antes de delegar cambios amplios o críticos.
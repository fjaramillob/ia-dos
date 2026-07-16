# Handoff entre Conversation Space y coding agent

Este flujo convierte una necesidad confirmada en una tarea acotada, verificable y trazable.

Consulta primero:

- [Registro de tópicos conversacionales](../orchestration/topic-routing-registry.md);
- [Registro de tipos de ejecución](../execution/execution-task-types.md).

## Flujo

```text
Conversation Space de origen
→ decisión o resultado esperado
→ tipo de ejecución
→ Execution Task
→ preparación local si hace falta
→ coding agent
→ cambios y verificaciones
→ Execution Report
→ regreso al espacio de origen
→ revisión e iteración
```

`00` no es una parada obligatoria entre definición y ejecución. El reporte vuelve primero al espacio que preparó la tarea.

## 1. Confirmar el tópico de origen

Antes de delegar, registra:

- tópico y nombre del Conversation Space;
- decisión que quedó confirmada;
- resultado verificable esperado;
- motivo por el que la ejecución debe regresar a ese espacio.

El tópico gobierna quién revisará el resultado, no qué herramienta concreta debe ejecutarlo.

## 2. Elegir el tipo de ejecución

Toda tarea debe declarar un tipo principal:

```text
INSPECT | BOOTSTRAP | BUILD | FIX | REFACTOR | MIGRATE
TEST | HARDEN | DOCUMENT | WIKI | RELEASE | OPERATE
```

Elige el tipo según el resultado dominante. No mezcles varios tipos para ocultar objetivos independientes.

El tipo aporta valores predeterminados sobre lectura, escritura, evidencia y detención, pero no concede permisos.

## 3. Preparar la Execution Task

Usa `templates/execution-task.template.md`. Debe incluir:

- tópico y espacio de origen;
- tipo de ejecución;
- espacio de retorno;
- objetivo único;
- contexto mínimo;
- alcance y fuera de alcance;
- repositorios y rutas autorizadas;
- capacidades y autorizaciones explícitas;
- criterios de aceptación;
- verificaciones y evidencia esperada;
- condiciones de detención;
- documentación o memoria a actualizar;
- formato del `Execution Report`.

La tarea debe poder ejecutarse sin reconstruir información desde varios mensajes.

## 4. Preparar el entorno

Si la ejecución requiere repositorios locales, archivos, Git o herramientas de desarrollo, indica previamente:

- qué repositorios deben estar disponibles;
- qué ruta o workspace se utilizará;
- qué instalación local es necesaria;
- qué accesos no deben entregarse;
- qué estado Git debe verificarse antes de escribir.

No prepares ni expongas todo el workspace por rutina.

## 5. Ejecutar con el coding agent

El agente debe:

1. confirmar tópico de origen, tipo, repositorios, ramas y rutas;
2. revisar instrucciones técnicas aplicables;
3. ejecutar `git status` antes de escribir;
4. inspeccionar el estado real;
5. respetar los defaults del tipo y las autorizaciones concretas;
6. modificar solo el alcance autorizado;
7. detenerse ante contradicciones o riesgos;
8. ejecutar verificaciones aplicables;
9. revisar el diff completo;
10. devolver un `Execution Report` al espacio indicado.

## 6. Revisar el Execution Report

El espacio de origen compara:

- tipo solicitado versus tipo realmente realizado;
- objetivo versus resultado;
- criterios versus evidencia;
- alcance versus diff;
- verificaciones solicitadas versus ejecutadas;
- autorizaciones versus acciones realizadas;
- estado declarado versus estado real;
- riesgos, bloqueos y decisiones pendientes.

Una afirmación del agente no sustituye evidencia.

## 7. Cerrar el ciclo

Después de aprobar el resultado:

- conserva implementación y evidencia en sus fuentes correspondientes;
- actualiza la Wiki cuando exista conocimiento durable confirmado;
- prepara una corrección o la siguiente tarea desde el mismo espacio;
- vuelve a `00` solo cuando haya una reorientación real.

## Rechaza el cierre cuando

- el reporte no identifica tópico, tipo o espacio de retorno;
- el tipo realizado no coincide y no existe justificación;
- faltan verificaciones exigidas sin explicación;
- los criterios no tienen evidencia;
- aparecen cambios fuera de alcance;
- el reporte no coincide con el diff o el estado Git;
- se tomaron decisiones o acciones no autorizadas;
- la documentación presenta propuestas como implementadas.

## Verificación final

- [ ] El tópico de origen está declarado.
- [ ] El tipo de ejecución representa el resultado dominante.
- [ ] El objetivo es único y terminable.
- [ ] El contexto es mínimo y suficiente.
- [ ] Las referencias pertenecen al proyecto actual.
- [ ] Alcance, fuera de alcance y rutas están explícitos.
- [ ] Los criterios y verificaciones son observables.
- [ ] Las autorizaciones están declaradas.
- [ ] El reporte vuelve al espacio de origen.
- [ ] La memoria durable tiene un destino definido.
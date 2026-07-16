# Handoff entre Conversation Space y coding agent

Este flujo convierte una necesidad confirmada en una tarea acotada, verificable y trazable.

No consiste en reenviar todo el historial del proyecto ni en pedir al agente que “resuelva lo necesario”.

## Flujo

```text
Conversation Space de origen
→ decisión o resultado esperado
→ Execution Task
→ preparación local si hace falta
→ coding agent
→ cambios y verificaciones
→ Execution Report
→ regreso al espacio de origen
→ revisión e iteración
```

`00` no es una parada obligatoria entre definición y ejecución. El reporte vuelve primero al espacio que preparó la tarea.

## Entradas mínimas

Antes de delegar, debe existir:

- objetivo confirmado;
- fuentes del proyecto actual;
- estado inicial conocido o una instrucción de inspección;
- alcance y fuera de alcance;
- repositorios y rutas autorizadas;
- criterios de aceptación verificables;
- pruebas o verificaciones aplicables;
- condiciones de detención;
- autorización explícita sobre escritura y cambios remotos.

No es obligatorio crear un `CORE` o Context Pack para una tarea pequeña si el prompt ya contiene contexto mínimo suficiente.

## Preparar la Execution Task

Usa `templates/execution-task.template.md` cuando aporte estructura. La tarea debe incluir:

- rol y entorno;
- objetivo;
- contexto mínimo;
- alcance;
- fuera de alcance;
- rutas autorizadas y prohibidas;
- capacidades requeridas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención;
- reglas de Git y cambios remotos;
- formato del `Execution Report`.

La tarea debe poder ejecutarse sin reconstruir información desde varios mensajes.

## Preparar el entorno

Si la ejecución requiere repositorios locales, archivos, Git o herramientas de desarrollo, indica previamente:

- qué repositorios deben estar disponibles;
- qué ruta o workspace se utilizará;
- qué instalación local es necesaria;
- qué accesos no deben entregarse;
- qué estado Git debe verificarse antes de escribir.

No prepares ni expongas todo el workspace por rutina.

## Ejecutar con el coding agent

El agente debe:

1. confirmar repositorios, ramas y rutas;
2. revisar instrucciones técnicas aplicables;
3. ejecutar `git status` antes de escribir;
4. inspeccionar el estado real;
5. modificar solo el alcance autorizado;
6. detenerse ante contradicciones o riesgos;
7. ejecutar verificaciones aplicables;
8. revisar el diff completo;
9. devolver un `Execution Report`.

## Revisar el Execution Report

El espacio de origen compara:

- objetivo versus resultado;
- criterios versus evidencia;
- alcance versus diff;
- verificaciones solicitadas versus ejecutadas;
- autorizaciones versus acciones realizadas;
- estado declarado versus estado real;
- riesgos, bloqueos y decisiones pendientes.

Una afirmación del agente no sustituye evidencia.

## Cerrar el ciclo

Después de aprobar el resultado:

- conserva implementación y evidencia en sus fuentes correspondientes;
- actualiza la Wiki cuando exista conocimiento durable confirmado;
- prepara una corrección o la siguiente tarea desde el mismo espacio;
- vuelve a `00` solo cuando haya una reorientación real.

## Rechaza el cierre cuando

- faltan verificaciones exigidas sin explicación;
- los criterios no tienen evidencia;
- aparecen cambios fuera de alcance;
- el reporte no coincide con el diff o el estado Git;
- se tomaron decisiones o acciones no autorizadas;
- la documentación presenta propuestas como implementadas.

## Verificación final

- [ ] El objetivo es único y terminable.
- [ ] El contexto es mínimo y suficiente.
- [ ] Las referencias pertenecen al proyecto actual.
- [ ] Alcance, fuera de alcance y rutas están explícitos.
- [ ] Los criterios y verificaciones son observables.
- [ ] Las autorizaciones están declaradas.
- [ ] El reporte vuelve al espacio de origen.
- [ ] La memoria durable tiene un destino definido.

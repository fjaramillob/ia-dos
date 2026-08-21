# Wiki Update Task — perfil de Execution Task

Usa este perfil cuando una `Execution Task` tenga como resultado principal actualizar memoria durable Markdown.

No crea un tipo de artefacto nuevo. Conserva el contrato canónico de ejecución.

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar alcance | resolver contradicciones conceptuales | aprobar el propio resultado | iniciar otra unidad
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID]
```

## Identificación

- Título: `[TÍTULO BREVE]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Execution Cell: `[WIKI SYNC O NO APLICA]`
- Destino del Execution Report: `[CONVERSATION SPACE]`
- Memory Bootstrap Gate: `[PASS | BOOTSTRAP REQUIRED — ESTA TAREA MATERIALIZA EL CHECKPOINT | NO APLICA]`
- Readiness indispensable: `[LISTO PARA EJECUCIÓN | NO APLICA]`

Si esta tarea responde a `BOOTSTRAP REQUIRED`, su único resultado es persistir el checkpoint durable mínimo necesario para desbloquear otra unidad. Esa unidad original queda fuera de alcance y su gate se reevalúa después de revisar el Execution Report del bootstrap.

## Objetivo documental

Describe el conocimiento durable que debe quedar creado, actualizado, corregido o retirado.

## Conocimiento confirmado

### Hechos vigentes

- `[HECHO]`

### Decisiones confirmadas

- `[DECISIÓN]`

### Decidido / aprobado pero no implementado

- `[ELEMENTO O NINGUNO]`

### Pendientes o desconocidos que deben preservarse como tales

- `[ELEMENTO]`

### Contradicciones conocidas

- `[CONTRADICCIÓN O NINGUNA]`

Una contradicción que cambie el contenido final activa condición de detención; el coding agent no la resuelve por cuenta propia.

En un bootstrap de memoria, el conocimiento confirmado puede venir del contexto conversacional autorizado precisamente porque todavía no existe como fuente durable. Conserva la procedencia y no inventes autoridad adicional.

## Fuentes y autoridad

| Recurso | Autoridad para | Acceso permitido | Referencia |
|---|---|---|---|
| `[RECURSO]` | `[ÁMBITO]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[RUTA, URL, COMMIT O FECHA]` |

Una conversación o Execution Report puede aportar evidencia, pero no se convierte automáticamente en estado oficial.

## Lectura requerida

- `AGENTS.md` de la Wiki, cuando exista;
- `.ia-dos.yaml`, cuando exista y corresponda;
- `[00-home.md O HOME REAL O NINGUNO SI EL BOOTSTRAP LO CREA]`;
- `[PÁGINAS CONCRETAS NECESARIAS O NINGUNA]`.

No leas toda la Wiki por defecto.

## Zonas autorizadas

- recurso de memoria: `[REPOSITORIO / DIRECTORIO / URL]`
- branch o modo: `[BRANCH / MODIFICACIÓN LOCAL / OTRO]`
- rutas modificables:
  - `[RUTA]`
- rutas prohibidas:
  - `[RUTA]`
- contenido que debe preservarse:
  - `[RUTA O DESCRIPCIÓN]`

## Alcance

### Incluido

- `[CAMBIO DOCUMENTAL AUTORIZADO]`

### Fuera de alcance

- cambiar decisiones no confirmadas;
- modificar implementación;
- mover TASK/REPORT a la Wiki por defecto;
- reorganizar páginas no necesarias para el objetivo;
- introducir dependencias de plugins o formatos propietarios;
- si responde a `BOOTSTRAP REQUIRED`, ejecutar la unidad original que busca desbloquear;
- `[OTRA EXCLUSIÓN]`.

## Capacidades y autorizaciones

- lectura: `[AUTORIZADA / NO AUTORIZADA]`
- escritura: `[AUTORIZADA / NO AUTORIZADA]`
- branch: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- commit: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- push: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- pull request: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- merge: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- otros recursos externos: `[AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]`

## Guardrails

- no inventar información;
- no convertir propuestas en hechos;
- no presentar como implementado algo sin evidencia técnica;
- priorizar estado vigente sobre historia;
- usar enlaces Markdown relativos para navegación canónica;
- no depender de Obsidian, wikilinks o plugins para semántica crítica;
- no duplicar fuentes de verdad sin necesidad;
- no eliminar contenido vigente sin justificación y alcance explícito;
- no guardar secretos ni datos no permitidos;
- no ampliar un bootstrap hacia la unidad que depende de él.

## Criterios de aceptación

- [ ] Las rutas autorizadas reflejan únicamente conocimiento confirmado.
- [ ] `Implementado`, `Decidido/no implementado`, `Pendiente`, `Fuera de alcance` y `Desconocido` no se confunden.
- [ ] El home o mapa de memoria sigue orientando correctamente cuando fue afectado.
- [ ] Los enlaces relativos modificados son coherentes.
- [ ] No se modificaron rutas fuera del alcance.
- [ ] El diff es revisable y no contiene secretos.
- [ ] Si es bootstrap, el checkpoint permite reevaluar la unidad original sin depender del chat para el conocimiento persistido.
- [ ] `[CRITERIO ESPECÍFICO]`.

## Validaciones requeridas

- revisión de Markdown;
- revisión de enlaces relativos afectados;
- validación de YAML cuando exista;
- revisión completa del diff;
- confirmación de archivos creados, modificados o eliminados;
- `[VALIDACIÓN ESPECÍFICA]`.

## Condiciones de detención

Detente y reporta cuando:

- falte una decisión necesaria;
- una contradicción cambie el contenido final;
- la memoria real no coincida con el contexto entregado de forma relevante;
- sea necesario tocar rutas o recursos no autorizados;
- aparezca trabajo previo que pueda perderse;
- una validación crítica falle;
- se detecten secretos o información sensible;
- la tarea requiera una reorganización mayor no aprobada;
- un bootstrap requiera inventar conocimiento o continuar con la unidad original.

## Entrega requerida

Devuelve un `Execution Report` canónico con:

- resultado observable;
- archivos creados, modificados o eliminados;
- fuentes consultadas;
- autorizaciones utilizadas;
- validaciones y evidencia;
- desviaciones o contradicciones;
- fuera de alcance preservado;
- pendientes del alcance original, si existen;
- atención concreta requerida o `Ninguna`.

El reporte describe la ejecución documental. No propone por defecto nuevo conocimiento durable adicional ni elige la decisión de gobierno posterior. No apruebes tu propio trabajo ni inicies otra unidad.

Si esta tarea materializó un checkpoint requerido por Memory Bootstrap, el Cycle Owner debe revisar el reporte y reevaluar el gate de la unidad original antes de emitirla.
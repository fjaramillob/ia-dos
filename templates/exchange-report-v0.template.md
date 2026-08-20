# IA-DOS — Exchange Execution Report v0

Exchange v0 conserva un `Execution Report` canónico usando el mismo identificador autocontenido del TASK asociado.

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: Aprobar y cerrar | Corregir | Revertir | Escalar | Revisar memoria
Forbidden Output: iniciar automáticamente otra tarea o ciclo
Cycle ID: NO APLICA | [MISMO CYCLE-ID DEL TASK]
Task ID: PROJECT-ORIGIN-CELL-YYYYMMDD-HHMMSS
Execution Cell: CELL
Cycle Owner: [CONVERSATION SPACE]
Título: [MISMO TÍTULO DEL TASK]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Decisión requerida: APROBAR Y CERRAR | CORREGIR | REVERTIR | ESCALAR | REVISAR MEMORIA | NINGUNA
```

El `Estado` describe el resultado de la ejecución. La `Decisión requerida` describe qué debe decidir después el Cycle Owner. No mezclar ambos conceptos.

## Resultado

Describir de forma breve y concreta qué se logró y cuál es el resultado observable.

Evitar narrar paso a paso el proceso seguido.

## Cambios realizados

Enumerar únicamente los cambios relevantes.

Cuando corresponda, incluir:

- archivos creados, modificados o eliminados;
- endpoints;
- migraciones;
- componentes;
- tests;
- configuración;
- acciones externas efectivamente realizadas.

No incluir diffs completos salvo solicitud explícita.

## Recursos y autorizaciones utilizadas

| Recurso | Acceso utilizado | Cambio o acción | Evidencia |
|---|---|---|---|
| `[RECURSO]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[CAMBIO O NINGUNO]` | `[EVIDENCIA]` |

Declarar únicamente capacidades efectivamente utilizadas. Una autorización concedida pero no usada no debe presentarse como acción realizada.

## Validación

Indicar cada comprobación ejecutada y su resultado.

Ejemplos:

- TypeScript: OK
- Lint: OK
- Tests: `N/N` aprobados
- Build: OK
- Validación manual: OK
- Smoke test: OK

Si una validación requerida no pudo ejecutarse, indicarlo explícitamente.

## Criterios de aceptación

- [ ] `[CRITERIO]` — `[EVIDENCIA]`

No marcar un criterio como cumplido sin evidencia suficiente.

## Fuera de alcance

Confirmar los elementos relevantes que permanecieron sin modificar.

- `[ELEMENTO]`

## Desviaciones o problemas

Indicar cualquier diferencia respecto del TASK original, por ejemplo:

- alcance que debió detenerse;
- comportamiento no previsto;
- dependencia faltante;
- limitación técnica;
- supuesto necesario;
- bloqueo;
- riesgo descubierto durante la ejecución.

Si no existieron desviaciones:

`Ninguna.`

## Pendientes

Indicar trabajo relacionado que quedó fuera de esta tarea.

Un pendiente no implica por sí mismo que la tarea esté incompleta.

Si no existen pendientes:

`Ninguno.`

## Conocimiento potencialmente durable

Indicar únicamente hechos nuevos descubiertos durante la ejecución que podrían ser relevantes para la memoria durable del proyecto.

No modificar la Wiki ni declarar estos hechos como conocimiento oficial salvo que la tarea lo haya autorizado expresamente.

Si no surgió conocimiento nuevo relevante:

`Ninguno.`

## Condiciones de detención activadas

- `Ninguna.`, o
- `[CONDICIÓN Y ACCIÓN TOMADA]`

## Decisión requerida

Repetir una sola decisión coherente con el encabezado y explicar brevemente cuando no sea evidente:

- `APROBAR Y CERRAR`
- `CORREGIR`
- `REVERTIR`
- `ESCALAR`
- `REVISAR MEMORIA`
- `NINGUNA`

El coding agent no aprueba su propio resultado ni inicia automáticamente la siguiente unidad.
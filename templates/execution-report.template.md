# Execution Report

El `Execution Report` registra evidencia de lo ejecutado. No decide por el Cycle Owner y no funciona como mecanismo de consolidación de memoria durable.

## Encabezado de retorno

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión y decisión del Cycle Owner
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El `Estado` describe únicamente el resultado de la ejecución.

`Atención requerida` identifica un bloqueo, riesgo, desviación o decisión concreta que el Cycle Owner deba revisar. No selecciona por adelantado una acción de gobierno como `APROBAR`, `CORREGIR`, `REVERTIR`, `ESCALAR` o `REVISAR MEMORIA`.

## Identificación

- Task ID: `[TASK-ID]`
- Cycle ID: `[CYCLE-ID O NO APLICA]`
- Título: `[TÍTULO]`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino del reporte: `[CONVERSATION SPACE]`
- Execution Cell o sesión: `[NOMBRE O NO APLICA]`
- Rol ejecutado: `Coding Agent — Execution`
- Tipo solicitado: `[TIPO]`
- Tipo realizado: `[TIPO]`
- Entorno: `[LOCAL / REMOTO / COMBINADO / OTRO]`
- Rama, versión o equivalente: `[REFERENCIA O NO APLICA]`
- Commit, cambio remoto o equivalente: `[REFERENCIA O NO APLICA]`
- Estado: `COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO`

Incluye rama, commit u otras referencias sólo cuando existan y sean relevantes para verificar la tarea. No agregues metadata de herramienta o modelo por rutina.

## Resultado

Describe qué se hizo y cuál es el resultado observable.

## Recursos utilizados

| Recurso | Rol | Acceso utilizado | Cambio realizado | Evidencia |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[CAMBIO O NINGUNO]` | `[EVIDENCIA]` |

## Artefactos modificados

- `[RUTA, RECURSO O IDENTIFICADOR]` — `[CAMBIO]`

Usa `Ninguno` cuando la tarea fue solo lectura.

## Instrucciones consultadas

- instrucciones locales aplicables;
- contrato IA-DOS embebido, remoto o local cuando corresponda;
- otras fuentes autorizadas necesarias para la tarea.

Declara `No disponible` cuando una instrucción requerida no pudo consultarse.

## Validación y evidencia

| Verificación | Resultado | Evidencia |
|---|---|---|
| `[PRUEBA O REVISIÓN]` | `Aprobada | Fallida | No ejecutada` | `[SALIDA, URL O DESCRIPCIÓN]` |

No marques una prueba como aprobada sin haberla ejecutado o revisado.

## Criterios de aceptación

- [ ] `[CRITERIO]` — `[EVIDENCIA]`

## Autorizaciones utilizadas

- lectura:
- escritura:
- control de versiones:
- cambios remotos:
- integración, despliegue o producción:
- datos, recursos externos o costes:

No declares una acción que no haya ocurrido.

## Fuera de alcance preservado

- `[ELEMENTO NO MODIFICADO]`

## Desviaciones o problemas

- `Ninguna`, o
- `[DESVIACIÓN, PROBLEMA, MOTIVO Y EFECTO]`

Indica cualquier diferencia entre la tarea aprobada y lo realmente ejecutado. No normalices una ampliación de alcance sólo porque el cambio ya ocurrió.

## Pendientes del alcance original

- `Ninguno`, o
- `[ELEMENTO QUE QUEDÓ SIN COMPLETAR]`

No uses esta sección como backlog general ni agregues trabajo futuro independiente.

## Condiciones de detención activadas

- `Ninguna`, o
- `[CONDICIÓN Y ACCIÓN TOMADA]`

## Atención requerida al Cycle Owner

- `Ninguna`, o
- `[PREGUNTA, BLOQUEO, RIESGO O DECISIÓN CONCRETA QUE REQUIERE REVISIÓN]`

Esta sección aporta información para la revisión. La decisión posterior pertenece exclusivamente al Cycle Owner.

Después de revisar la evidencia, el Cycle Owner puede aprobar y cerrar, corregir, revertir, escalar o evaluar si corresponde actualizar memoria durable. Esas acciones no las decide ni las marca el coding agent dentro del Execution Report.

## Frontera con memoria durable

El Execution Report puede contener hechos y evidencia descubiertos durante la ejecución porque forman parte del resultado observado, pero no debe crear una sección paralela de “conocimiento durable” ni recomendar automáticamente qué incorporar a la Wiki.

La evaluación de qué conocimiento merece consolidación ocurre después de la revisión del reporte, bajo gobierno conversacional y, cuando aporta, `90 — Wiki y memoria`.

## Declaración final

- [ ] Revisé los cambios completos o confirmé que no hubo escritura.
- [ ] Reporté verificaciones ejecutadas y omitidas.
- [ ] No oculté fallos ni trabajo incompleto.
- [ ] No amplié alcance sin autorización.
- [ ] Respeté la autoridad y acceso de cada recurso.
- [ ] No expuse secretos o datos sensibles.
- [ ] No cambié el Cycle Owner ni abrí otro ciclo.
- [ ] No aprobé mi propio resultado ni elegí la decisión de gobierno posterior.
- [ ] Este reporte vuelve al destino indicado.
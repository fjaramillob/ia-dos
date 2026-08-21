# Execution Report

El `Execution Report` registra evidencia de lo ejecutado. No decide por el Cycle Owner, no sustituye la aprobación humana aplicable y no funciona como mecanismo de consolidación de memoria durable.

## Encabezado de retorno

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión de evidencia bajo la autoridad aplicable
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El `Estado` describe únicamente el resultado de la ejecución.

`Atención requerida` identifica un bloqueo, riesgo, desviación o decisión concreta que requiere revisión. No selecciona por adelantado `APROBAR`, `CORREGIR`, `REVERTIR`, `ESCALAR` o `REVISAR MEMORIA`.

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

Incluye metadata técnica sólo cuando exista y sea relevante para verificar la tarea.

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
- otras fuentes autorizadas necesarias.

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

Indica cualquier diferencia entre la tarea autorizada y lo realmente ejecutado. No normalices una ampliación de alcance sólo porque ya ocurrió.

## Pendientes del alcance original

- `Ninguno`, o
- `[ELEMENTO QUE QUEDÓ SIN COMPLETAR]`

No uses esta sección como backlog general ni agregues trabajo futuro independiente.

## Condiciones de detención activadas

- `Ninguna`, o
- `[CONDICIÓN Y ACCIÓN TOMADA]`

## Atención requerida

- `Ninguna`, o
- `[PREGUNTA, BLOQUEO, RIESGO O DECISIÓN CONCRETA QUE REQUIERE REVISIÓN]`

Esta sección aporta información a la revisión y no preselecciona la decisión posterior.

## Revisión posterior

Después de revisar la evidencia, el Cycle Owner puede cerrar, corregir, revertir, transferir, escalar o continuar **dentro de la autoridad delegada**.

La persona responsable conserva la aprobación final cuando la decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

Estas acciones no las decide ni las marca el coding agent dentro del Execution Report.

## Frontera con memoria durable

El reporte puede contener hechos y evidencia descubiertos durante la ejecución porque forman parte del resultado observado, pero no crea una sección paralela de “conocimiento durable” ni recomienda automáticamente qué incorporar a la LLM Wiki.

La evaluación de memoria ocurre después de revisar el reporte. Si un hecho nuevo merece persistirse, se autoriza una actualización documental separada, salvo que la propia Execution Task ya incluyera una actualización durable concreta.

## Declaración final

- [ ] Revisé los cambios completos o confirmé que no hubo escritura.
- [ ] Reporté verificaciones ejecutadas y omitidas.
- [ ] No oculté fallos ni trabajo incompleto.
- [ ] No amplié alcance sin autorización.
- [ ] Respeté autoridad y acceso de cada recurso.
- [ ] No expuse secretos o datos sensibles.
- [ ] No cambié Cycle Owner ni abrí otro ciclo.
- [ ] No aprobé mi propio resultado ni elegí la decisión de gobierno posterior.
- [ ] No recomendé memoria durable o una siguiente unidad por rutina.
- [ ] Este reporte vuelve al destino indicado.

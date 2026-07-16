# Execution Report

## Identificación

- Task ID: `[TASK-ID]`
- Título: `[TÍTULO]`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino del reporte: `[CONVERSATION SPACE]`
- Espacio de escalamiento: `[NORMALMENTE 00 — DIRECCIÓN Y ORQUESTACIÓN]`
- Tipo solicitado: `[TIPO]`
- Tipo realizado: `[TIPO]`
- Entorno: `[LOCAL / REMOTO / COMBINADO / OTRO]`
- Rama, versión o equivalente: `[REFERENCIA O NO APLICA]`
- Commit, cambio remoto o equivalente: `[REFERENCIA O NO APLICA]`
- Estado: `Completada | Parcial | Bloqueada | No iniciada`

## Resumen

Describe qué se hizo y cuál es el resultado observable.

## Recursos utilizados

| Recurso | Rol | Acceso utilizado | Cambio realizado | Evidencia |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[CAMBIO O NINGUNO]` | `[EVIDENCIA]` |

## Artefactos modificados

- `[RUTA, RECURSO O IDENTIFICADOR]` — `[CAMBIO]`

Usa `Ninguno` cuando la tarea fue solo lectura.

## Pruebas y evidencia

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

## Fuera de alcance

- `[ELEMENTO NO MODIFICADO]`

## Desviaciones

- `Ninguna`, o
- `[DESVIACIÓN, MOTIVO Y APROBACIÓN]`

Indica si el tipo o el objetivo cambiaron durante el trabajo.

## Gate de tamaño observado

- [ ] La tarea conservó un solo resultado.
- [ ] No se ejecutaron fases adicionales no autorizadas.
- [ ] El trabajo nuevo detectado se dejó como siguiente unidad y no se incorporó silenciosamente.

## Riesgos, limitaciones y decisiones pendientes

- `[ELEMENTO]`

## Condiciones de detención activadas

- `Ninguna`, o
- `[CONDICIÓN Y ACCIÓN]`

## Actualización durable recomendada

- `[RECURSO O CONOCIMIENTO]`

No presentes propuestas como implementación.

## Próxima acción recomendada

Propón una sola acción verificable al Cycle Owner.

No escales a `00` salvo que exista reorientación, conflicto entre dominios, expansión importante de alcance o decisión estratégica.

## Declaración final

- [ ] Revisé los cambios completos o confirmé que no hubo escritura.
- [ ] Reporté verificaciones ejecutadas y omitidas.
- [ ] No oculté fallos ni trabajo incompleto.
- [ ] No amplié alcance sin aprobación.
- [ ] Respeté la autoridad y acceso de cada recurso.
- [ ] No expuse secretos o datos sensibles.
- [ ] Este reporte vuelve al destino indicado.
# Execution Task compacta

Usa este bloque como salida operativa por defecto cuando el resultado está definido, el Memory Bootstrap Gate está satisfecho cuando aplica, el entorno está `LISTO PARA EJECUCIÓN` cuando requiere readiness y existe la autorización aplicable.

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: trabajo fuera de alcance | autoaprobación | siguiente unidad

Método: IA-DOS
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [EXEC-ID]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Destino: [CONVERSATION SPACE]
Tipo: [INSPECT | BOOTSTRAP | BUILD | FIX | REFACTOR | MIGRATE | TEST | HARDEN | DOCUMENT | WIKI | RELEASE | OPERATE]

OBJETIVO ÚNICO
[RESULTADO CONCRETO, TERMINABLE Y VERIFICABLE]

PRECONDICIONES
- Memory Bootstrap Gate: [PASS | NO APLICA]
- Readiness indispensable: [LISTO PARA EJECUCIÓN | NO APLICA]
- Planning previo: [REFERENCIA APROBADA | NO APLICA]
- autorización humana adicional requerida: [RESUELTA | NO APLICA]

FUENTES DE AUTORIDAD
| Recurso o documento | Rol | Autoridad para | Acceso | Vigencia o referencia |
|---|---|---|---|---|
| [RECURSO] | [MEMORIA DURABLE / IMPLEMENTACIÓN / EVIDENCIA / REFERENCIA] | [ÁMBITO] | [LECTURA / ESCRITURA / ACCIÓN] | [RUTA, VERSIÓN, COMMIT O FECHA] |

ARTEFACTO PREVIO VÁLIDO
- [IMPLEMENTATION PLAN REVISADO, READINESS REPORT, EXECUTION REPORT O NO APLICA]

DELTA DEL CICLO
- [DECISIÓN O CAMBIO QUE HABILITA ESTA EJECUCIÓN]
- [EVIDENCIA ACTUAL]
- [BLOQUEO RESUELTO]
- [TRABAJO QUE DEBE PRESERVARSE]

No vuelvas a narrar el proyecto. Lee las fuentes declaradas y usa este delta como contexto activo.

ALCANCE AUTORIZADO
Incluido:
- [CAMBIO AUTORIZADO]

Fuera de alcance:
- [CAMBIO NO AUTORIZADO]

ZONAS
- modificables: [RECURSOS O RUTAS]
- prohibidas: [RECURSOS O RUTAS]
- rama o modo: [RAMA / MODIFICACIÓN LOCAL / OTRO]

CAPACIDADES Y AUTORIZACIONES
- lectura: [AUTORIZADA / NO AUTORIZADA]
- escritura: [AUTORIZADA / NO AUTORIZADA]
- branch: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- commit: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- push: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- pull request: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- merge: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- despliegue o producción: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- datos, servicios externos o costes: [AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]

CRITERIOS DE ACEPTACIÓN
- [ ] [RESULTADO OBSERVABLE]

VERIFICACIONES
- [COMANDO, REVISIÓN O PROCEDIMIENTO]
- evidencia esperada: [SALIDA O PRUEBA]

INSTRUCCIONES LOCALES
- [AGENTS.md, ARCHIVO EQUIVALENTE O NO EXISTEN]

CONDICIONES DE DETENCIÓN
Detente cuando falte información crítica, una fuente contradiga el estado real, una referencia no sea accesible o vigente, aparezca trabajo previo que pueda perderse, sea necesario tocar una zona o usar una capacidad no autorizada, falle una verificación crítica, exista riesgo de seguridad, datos o coste, o la tarea revele resultados independientes.

FALLBACK DE CONTEXTO
Cuando una fuente durable no sea accesible, usa sólo el extracto indispensable contenido en la tarea, conserva la referencia original y reporta la limitación. No compenses el acceso faltante ampliando alcance.

CONTRATO DE RETORNO
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión de evidencia bajo la autoridad aplicable
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
Execution Task ID: [EXEC-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]

Devuelve resultado observable, recursos modificados, fuentes consultadas, permisos utilizados, validaciones y evidencia, límites respetados, desviaciones, pendientes del alcance original y cualquier atención concreta que requiera revisión. No elijas la decisión de gobierno posterior, no consolides memoria durable y no inicies otra unidad.
```

## Regla de continuidad

Cuando el proyecto use una Execution Cell, reutiliza su conversación activa mientras siga respondiendo bien. No cambies el nombre de la célula ni abras una conversación nueva sólo porque cambia el resultado.

Los permisos no se heredan: cada Execution Task vuelve a declararlos aunque use la misma célula.

## Regla de autoridad

El Cycle Owner prepara o valida la tarea dentro de autoridad delegada. La persona responsable conserva la aprobación final cuando cambian dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

## Regla de compresión

Aplica `docs/orchestration/context-compression-by-authority.md`.

La memoria durable contiene contexto estable. La tarea transporta referencias precisas, delta vigente y contrato operativo completo. Permisos, límites y condiciones de detención nunca se omiten por compresión.

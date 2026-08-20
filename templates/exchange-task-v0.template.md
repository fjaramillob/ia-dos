# IA-DOS — Exchange Execution Task v0

Exchange v0 conserva una `Execution Task` canónica usando un identificador autocontenido y un formato compacto para intercambio manual persistente.

Este perfil no introduce una máquina de estados. La presencia del archivo en `inbox/` indica únicamente que forma parte del flujo activo de Exchange.

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar alcance | autoaprobar | iniciar otra unidad
Cycle ID: NO APLICA | [CYCLE-ID SI EL PROYECTO YA USA UNO]
Task ID: PROJECT-ORIGIN-CELL-YYYYMMDD-HHMMSS
Execution Cell: CELL
Cycle Owner: [CONVERSATION SPACE]
Destino del reporte: [CONVERSATION SPACE]
Título: [TÍTULO BREVE]
Origen: [00 | 10 | 20 | 30 | 40 | 50 | 90 | OTRO DOMINIO AUTORIZADO]
```

Nombre de archivo recomendado:

```text
PROJECT-ORIGIN-CELL-YYYYMMDD-HHMMSS-TASK.md
```

El título humano vive dentro del archivo y no forma parte del ID ni del nombre de archivo.

## Objetivo

Describir el resultado concreto, terminable y verificable que debe conseguirse.

Expresa qué debe quedar resuelto, no la historia que originó la instrucción.

## Contexto durable necesario

Incluir únicamente hechos vigentes necesarios para ejecutar correctamente esta tarea.

Este bloque es el extracto seleccionado por el Orchestrator cuando no conviene exigir lectura directa de toda la memoria durable.

Si no se requiere contexto adicional:

`Ninguno.`

## Referencias de autoridad

Declarar únicamente los recursos relevantes para esta ejecución.

| Recurso | Rol | Autoridad para | Acceso | Referencia |
|---|---|---|---|---|
| `[RECURSO]` | `[MEMORIA / IMPLEMENTACIÓN / EVIDENCIA / REFERENCIA]` | `[ÁMBITO]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[RUTA, COMMIT, VERSIÓN O FECHA]` |

No usar una referencia genérica como `ver Wiki` cuando una ruta concreta sea necesaria.

## Lectura requerida

Indicar exclusivamente documentos que el ejecutor debe leer antes de realizar la tarea.

Las referencias de autoridad o Wiki no implican lectura automática.

Si el TASK ya contiene todo el contexto necesario:

`Ninguna.`

## Instrucción

Describir qué debe realizar el ejecutor.

La instrucción debe permitir decisiones locales de implementación que puedan resolverse correctamente inspeccionando las fuentes autorizadas, sin conceder autoridad para redefinir producto, arquitectura, alcance o seguridad.

## Alcance autorizado

Incluido:

- `[CAMBIO AUTORIZADO]`

Fuera de alcance:

- `[CAMBIO NO AUTORIZADO]`

Zonas modificables:

- `[RUTA, RECURSO O ÁMBITO]`

Zonas prohibidas:

- `[RUTA, RECURSO O ÁMBITO]`

## Capacidades y acciones externas

Declarar sólo las relevantes para esta tarea.

- lectura: `[AUTORIZADA / NO AUTORIZADA]`
- escritura: `[AUTORIZADA / NO AUTORIZADA]`
- branch: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- commit: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- push: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- pull request: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- merge: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- despliegue o producción: `[AUTORIZADO / NO AUTORIZADO / NO APLICA]`
- datos, servicios externos o costes: `[AUTORIZACIÓN EXPLÍCITA / NO AUTORIZADO / NO APLICA]`

Una autorización de una tarea anterior no se hereda.

## Restricciones

Agregar únicamente restricciones específicas que no estén ya expresadas por alcance o capacidades.

Por defecto:

- no alterar decisiones de producto o arquitectura vigentes;
- no presentar como implementado aquello que sólo esté decidido o planificado;
- no modificar memoria durable como consecuencia automática de una implementación salvo autorización explícita;
- no incorporar resultados independientes descubiertos durante la ejecución.

## Criterios de aceptación

- [ ] `[RESULTADO OBSERVABLE]`
- [ ] `[RESULTADO OBSERVABLE]`

## Verificaciones

- `[COMANDO, REVISIÓN O PROCEDIMIENTO]`
- evidencia esperada: `[SALIDA O PRUEBA]`

Si una verificación no puede ejecutarse, debe reportarse explícitamente.

## Condiciones de detención

Detenerse cuando:

- falte información crítica;
- una fuente autorizada contradiga el estado real;
- exista trabajo previo que pueda perderse;
- sea necesario tocar una zona o usar una capacidad no autorizada;
- falle una verificación crítica;
- aparezca un riesgo relevante de seguridad, datos o coste;
- la tarea revele resultados independientes que deban convertirse en otra unidad.

## Referencias Wiki

Rutas relacionadas para trazabilidad y navegación. **Referenciar no significa leer.**

- `[RUTA]`

Si no corresponde:

`Ninguna.`

## Resultado esperado

Devuelve un `Execution Report` con exactamente el mismo `Task ID`.

El reporte debe separar:

- estado de ejecución;
- resultado y cambios;
- validaciones y evidencia;
- desviaciones, problemas y pendientes;
- conocimiento potencialmente durable;
- decisión requerida del Cycle Owner.

No apruebes tu propio resultado ni inicies otra tarea.

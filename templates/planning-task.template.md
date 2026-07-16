# Planning Task

Usa esta plantilla cuando el coding agent deba inspeccionar y proponer cómo implementar antes de autorizar escritura.

## Identificación

- ID: `[PLAN-ID]`
- Proyecto: `[NOMBRE]`
- Estado: `Propuesta | Aprobada | En análisis | Bloqueada | Completada | Cancelada`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino del Implementation Plan: `[CONVERSATION SPACE]`
- Espacio de escalamiento: `[CONVERSATION SPACE, NORMALMENTE 00]`
- Coding agent o entorno: `[ROL O HERRAMIENTA DISPONIBLE]`

## Objetivo del plan

Describe qué debe poder decidir el Cycle Owner después de revisar el plan.

## Contexto mínimo

- decisiones aceptadas;
- evidencia inicial;
- restricciones no negociables;
- incógnitas relevantes;
- trabajo que debe preservarse.

## Autoridad de fuentes, artefactos y entornos

| Recurso | Rol | Autoridad para | Acceso permitido | Limitaciones |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `Lectura` | `[LÍMITES]` |

La Planning Task es de solo lectura. Una excepción requiere una tarea distinta y autorización explícita.

## Inspección requerida

- estado real de los recursos autorizados;
- estructura, convenciones y dependencias relevantes;
- contradicciones entre fuentes;
- riesgos, bloqueos y decisiones abiertas;
- verificaciones disponibles;
- unidades de implementación posibles.

Adapta la inspección al proyecto. No conviertas esta lista en una auditoría exhaustiva por defecto.

## Resultado requerido

Devuelve un `Implementation Plan` usando `implementation-plan.template.md`.

Debe permitir:

- comprender el estado comprobado;
- distinguir hechos, inferencias y propuestas;
- decidir el resultado final verificable;
- dividir el trabajo en unidades dependientes;
- aprobar solo la primera Execution Task;
- identificar decisiones humanas y condiciones de detención.

## Fuera de alcance

- modificar artefactos;
- crear commits o cambios remotos;
- desplegar;
- crear recursos externos;
- generar costes;
- presentar propuestas como implementación;
- ampliar el objetivo sin aprobación.

## Gate de tamaño

Cada unidad propuesta debe poder completarse, verificarse y reportarse por separado sin mezclar resultados independientes.

## Condiciones de detención

Detente y reporta cuando:

- falte una fuente crítica;
- el acceso disponible no permita inspección suficiente;
- exista riesgo de exponer secretos o datos sensibles;
- aparezca una contradicción que requiera decisión humana;
- el resultado solicitado pertenezca realmente a otro dominio;
- preparar el plan exija escribir o ejecutar una acción no autorizada.

## Declaración final obligatoria

```text
No se modificaron artefactos.
No se realizaron cambios remotos ni despliegues.
El plan no constituye autorización de ejecución.
El Implementation Plan debe volver al destino indicado.
```
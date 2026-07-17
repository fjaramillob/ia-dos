# Planning Task

Usa esta plantilla cuando el coding agent deba inspeccionar y proponer cómo implementar antes de autorizar escritura.

## Identificación

- ID: `[PLAN-ID]`
- Proyecto: `[NOMBRE]`
- Estado: `Propuesta | Aprobada | En análisis | Bloqueada | Completada | Cancelada`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino del Implementation Plan: `[NORMALMENTE EL CYCLE OWNER]`
- Espacio de escalamiento: `[CONVERSATION SPACE, NORMALMENTE 00]`
- Coding agent o entorno: `[ROL O HERRAMIENTA DISPONIBLE]`

## Objetivo del plan

Describe una sola decisión que el Cycle Owner debe poder tomar después de revisar el plan.

Una Planning Task no debe pedir simultáneamente una auditoría completa, una arquitectura final, un roadmap y el diseño de todas las unidades futuras.

## Umbral de acción

Confirma:

- [ ] las fuentes disponibles permiten inspeccionar el estado real;
- [ ] existe suficiente contexto para proponer al menos una primera unidad segura;
- [ ] las incógnitas restantes pueden tratarse como supuestos, alternativas o decisiones posteriores;
- [ ] no existe una decisión humana indispensable que cambie el objetivo, los límites o la seguridad del plan.

Cuando las tres primeras condiciones se cumplen y la cuarta no bloquea, la salida correcta es esta Planning Task para el coding agent, no otra conversación.

## Gate de alcance de planificación

Confirma:

- [ ] existe una sola incertidumbre técnica dominante;
- [ ] la inspección solicitada es la mínima necesaria para resolverla;
- [ ] las áreas listadas están directamente relacionadas con esa decisión;
- [ ] los artefactos extensos ya existentes se referencian en vez de copiarse;
- [ ] el plan puede cerrarse sin diseñar toda la iniciativa.

Cuando alguna respuesta sea negativa, divide la Planning Task o reduce su objetivo.

## Contexto mínimo

- decisiones aceptadas;
- evidencia inicial;
- restricciones no negociables;
- incógnita técnica dominante;
- trabajo que debe preservarse.

## Autoridad de fuentes, artefactos y entornos

| Recurso | Rol | Autoridad para | Acceso permitido | Limitaciones |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `Lectura` | `[LÍMITES]` |

La Planning Task es de solo lectura. Una excepción requiere una tarea distinta y autorización explícita.

## Inspección requerida

Solicita únicamente lo necesario para responder la decisión dominante:

- estado real de los recursos relevantes;
- convenciones y dependencias que condicionan la decisión;
- contradicciones entre fuentes aplicables;
- riesgos y bloqueos directos;
- verificaciones disponibles;
- una primera unidad de implementación candidata, cuando corresponda.

No conviertas esta sección en una auditoría exhaustiva por defecto. Si aparece otra brecha independiente, declárala sin desarrollarla.

## Resultado requerido

Devuelve un `Implementation Plan` proporcional al objetivo.

Debe permitir:

- comprender el estado comprobado relevante;
- distinguir hechos, inferencias y propuestas;
- resolver o acotar la decisión técnica dominante;
- identificar dependencias indispensables;
- proponer una primera unidad pequeña cuando exista claridad;
- entregar una `Execution Task` candidata lista para revisión cuando esa primera unidad pueda definirse con seguridad;
- declarar decisiones humanas o de otro dominio sin resolverlas silenciosamente.

No es obligatorio producir un roadmap completo ni dividir toda la iniciativa cuando la Planning Task solo busca resolver una decisión puntual.

## Fuera de alcance

- modificar artefactos;
- crear commits o cambios remotos;
- desplegar;
- crear recursos externos;
- generar costes;
- presentar propuestas como implementación;
- ampliar el objetivo sin aprobación;
- resolver decisiones de otro dominio;
- repetir auditorías durables suficientes sin una brecha de evidencia concreta;
- bloquear el plan por preguntas que no impiden diseñar una primera unidad segura.

## Gate de tamaño

El Implementation Plan debe ser tan pequeño como permita tomar la siguiente decisión. Cada unidad propuesta debe poder completarse, verificarse y reportarse por separado.

## Condiciones de detención

Detente y reporta cuando:

- falte una fuente crítica;
- el acceso disponible no permita inspección suficiente;
- exista riesgo de exponer secretos o datos sensibles;
- aparezca una contradicción que requiera decisión humana indispensable antes de planificar;
- el resultado solicitado pertenezca realmente a otro dominio;
- preparar el plan exija escribir o ejecutar una acción no autorizada;
- la inspección comience a expandirse hacia objetivos independientes.

No te detengas por decisiones que puedan mantenerse explícitamente como supuesto, alternativa o decisión posterior sin comprometer la seguridad de la primera unidad.

## Declaración final obligatoria

```text
No se modificaron artefactos.
No se realizaron cambios remotos ni despliegues.
El plan no constituye autorización de ejecución.
El Implementation Plan debe volver al destino indicado.
Las brechas de otros dominios fueron declaradas, no resueltas silenciosamente.
La primera Execution Task candidata fue incluida cuando existió evidencia suficiente.
```

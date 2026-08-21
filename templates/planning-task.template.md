# Planning Task

Usa esta plantilla cuando el coding agent deba inspeccionar y proponer cómo implementar antes de autorizar escritura.

## Identificación

- Cycle ID: `[CYCLE-ID O NO APLICA]`
- ID: `[PLAN-ID]`
- Proyecto: `[NOMBRE]`
- Estado: `Propuesta | Aprobada | En análisis | Bloqueada | Completada | Cancelada`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Preparada por: `[CONVERSATION SPACE]`
- Ejecutada por: `[CODING AGENT O ENTORNO TÉCNICO]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Sesión de planificación, cuando aporte: `PLAN — [RESULTADO] | NO APLICA`
- Rol activo: `Coding Agent — Planning`
- Destino del Implementation Plan: `[CONVERSATION SPACE]`
- Espacio de escalamiento: `[NORMALMENTE 00]`
- Acceso a IA-DOS: `Embedded Contract | Remote Repository | Local Reference`

Incluye `templates/agent-role-contract.template.md` como contrato embebido cuando aporte.

## Contrato de salida

La Planning Task se entrega al coding agent y vuelve al mismo Cycle Owner.

```text
Conversation Space prepara
→ Coding Agent — Planning inspecciona en solo lectura
→ Implementation Plan
→ Cycle Owner revisa
```

Un identificador `PLAN — ...` puede ayudar a organizar una herramienta, pero no obliga a abrir una conversación de planificación nueva por cada tarea.

La futura ejecución requiere una autorización separada. Esa separación de autoridad **no exige** una sesión de ejecución nueva: si existe una Execution Cell adecuada, la Execution Task puede reutilizar su conversación activa sin heredar permisos.

## Objetivo del plan

Describe una sola decisión que el Cycle Owner debe poder revisar después del plan.

No pidas simultáneamente auditoría completa, arquitectura final, roadmap y diseño de todas las unidades futuras.

## Umbral de acción

Confirma:

- [ ] las fuentes autorizadas permiten inspeccionar el estado real;
- [ ] existe suficiente contexto para proponer al menos una primera unidad segura;
- [ ] las incógnitas restantes pueden tratarse como supuestos, alternativas o decisiones posteriores;
- [ ] no existe una decisión humana indispensable que cambie objetivo, límites, autoridad o seguridad del plan.

## Gate de alcance

- [ ] existe una sola incertidumbre técnica dominante;
- [ ] la inspección es la mínima necesaria;
- [ ] las áreas listadas están directamente relacionadas;
- [ ] artefactos extensos se referencian en vez de copiarse;
- [ ] el plan puede cerrarse sin diseñar toda la iniciativa.

Si no, reduce o divide la Planning Task.

## Contexto mínimo

- decisiones aceptadas;
- evidencia inicial;
- restricciones no negociables;
- incógnita técnica dominante;
- trabajo que debe preservarse.

No copies toda la historia del proyecto.

## Autoridad de fuentes, artefactos y entornos

| Recurso | Rol | Autoridad para | Acceso permitido | Limitaciones |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `Lectura` | `[LÍMITES]` |

La Planning Task es de solo lectura. Una necesidad de escritura requiere otra tarea y autorización explícita.

## Acceso al método

La tarea debe ser autosuficiente.

- usa contrato embebido cuando corresponda;
- consulta fuente remota cuando esté disponible;
- usa referencia local compartida cuando haya sido declarada;
- no clones IA-DOS silenciosamente ni dentro del producto.

## Inspección requerida

Solicita sólo lo necesario:

- instrucciones locales aplicables;
- estado real de recursos relevantes;
- convenciones y dependencias que condicionan la decisión;
- contradicciones entre fuentes;
- riesgos y bloqueos directos;
- verificaciones disponibles;
- una primera unidad candidata cuando corresponda.

Cada hallazgo que condicione la decisión debe incluir recurso, ruta o referencia, estado observado e interpretación. Lo no demostrado se marca como inferencia o propuesta.

## Resultado requerido

Devuelve un `Implementation Plan` proporcional que permita:

- comprender estado comprobado relevante;
- separar hechos, inferencias y propuestas;
- resolver o acotar la decisión técnica dominante;
- identificar dependencias indispensables;
- proponer una primera unidad pequeña;
- entregar una `Execution Task` candidata cuando sea segura;
- declarar decisiones humanas o de otro dominio sin resolverlas silenciosamente.

La Execution Task candidata debe indicar `Execution Cell o sesión: [NOMBRE O NO APLICA]` y reutilizar una célula existente cuando corresponda; no derives el nombre de la sesión desde el resultado por defecto.

**No asignes el Task ID de la candidata.** Declara `Task ID: PENDIENTE — ASIGNAR AL ADOPTAR`. El Conversation Agent/Cycle Owner asigna la identidad cuando revisa y adopta la candidata como Execution Task real.

## Fuera de alcance

- modificar artefactos;
- crear commits o cambios remotos;
- desplegar;
- crear recursos externos o costes;
- presentar propuestas como implementación;
- ampliar el objetivo;
- resolver decisiones de otro dominio;
- abrir otro Conversation Space sólo para ejecutar esta Planning Task;
- aprobar o ejecutar la Execution Task candidata;
- asignar el Task ID de una futura Execution Task;
- cambiar el Cycle Owner;
- clonar IA-DOS sin autorización.

## Condiciones de detención

Detente cuando:

- falte una fuente crítica;
- el acceso no permita inspección suficiente;
- exista riesgo de secretos o datos sensibles;
- una contradicción requiera decisión humana indispensable;
- preparar el plan exija escritura no autorizada;
- la inspección se expanda a objetivos independientes.

No te detengas por decisiones que puedan mantenerse como supuesto reversible sin comprometer la seguridad de la primera unidad.

## Encabezado de retorno

```text
Artifact Type: Implementation Plan
Planning Task ID: [PLAN-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Sesión de planificación: [PLAN — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
```

El Implementation Plan propone. La decisión de aprobar, corregir, rechazar o escalar pertenece al Cycle Owner dentro de la autoridad delegada y a la persona responsable cuando corresponda.

## Declaración final

```text
No se modificaron artefactos.
No se realizaron cambios remotos ni despliegues.
El plan no constituye autorización de ejecución.
El Implementation Plan vuelve al Cycle Owner indicado.
La primera Execution Task candidata fue incluida cuando existió evidencia suficiente.
El Task ID de la candidata quedó pendiente para el Conversation Agent/Cycle Owner.
La futura ejecución conserva una autorización separada, pero no exige una conversación nueva si existe una Execution Cell válida.
```

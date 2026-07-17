# Planning Task

Usa esta plantilla cuando el coding agent deba inspeccionar y proponer cómo implementar antes de autorizar escritura.

## Identificación

- Cycle ID: `[CYCLE-ID]`
- ID: `[PLAN-ID]`
- Proyecto: `[NOMBRE]`
- Estado: `Propuesta | Aprobada | En análisis | Bloqueada | Completada | Cancelada`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Preparada por: `[CONVERSATION SPACE ESPECIALISTA]`
- Ejecutada por: `[CODING AGENT O ENTORNO TÉCNICO DISPONIBLE]`
- Revisada por: `[CYCLE OWNER, NORMALMENTE EL MISMO ESPECIALISTA]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Agent Session: `PLAN — [RESULTADO]`
- Rol activo: `Coding Agent — Planning`
- Destino del Implementation Plan: `[NORMALMENTE EL CYCLE OWNER]`
- Espacio de escalamiento: `[CONVERSATION SPACE, NORMALMENTE 00]`
- Acceso a IA-DOS: `Embedded Contract | Remote Repository | Local Reference`
- Referencia local de IA-DOS: `[RUTA O NO DISPONIBLE]`

Incluye `templates/agent-role-contract.template.md` como contrato embebido.

## Contrato de salida rápida

La Planning Task se entrega directamente al coding agent. No se abre otro Conversation Space para que ese chat la ejecute.

```text
especialista prepara
→ sesión PLAN — [RESULTADO]
→ coding agent inspecciona
→ Implementation Plan
→ especialista revisa
```

La sesión de planificación es independiente de cualquier futura sesión de ejecución.

Un Conversation Space solo puede ejecutar esta Planning Task cuando se cumplan todas las condiciones de autoejecución definidas por IA-DOS.

## Objetivo del plan

Describe una sola decisión que el Cycle Owner debe poder tomar después de revisar el plan.

Una Planning Task no debe pedir simultáneamente una auditoría completa, una arquitectura final, un roadmap y el diseño de todas las unidades futuras.

## Umbral de acción

Confirma:

- [ ] las fuentes disponibles permiten al coding agent inspeccionar el estado real;
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

## Acceso al método

La tarea debe ser autosuficiente.

- usa el contrato embebido siempre;
- consulta la fuente remota cuando esté disponible;
- usa una referencia local compartida cuando haya sido declarada;
- no clones IA-DOS dentro del repositorio del producto;
- no realices un clon silencioso;
- si se requiere crear una referencia local, solicita autorización explícita.

Una configuración local válida, no obligatoria, es:

```text
Proyectos/
├── 00-ia-dos/
└── [Proyecto]/
    ├── [proyecto-app]/
    └── [proyecto-wiki]/
```

## Inspección requerida

Solicita únicamente lo necesario para responder la decisión dominante:

- instrucciones locales aplicables;
- estado real de los recursos relevantes;
- convenciones y dependencias que condicionan la decisión;
- contradicciones entre fuentes aplicables;
- riesgos y bloqueos directos;
- verificaciones disponibles;
- una primera unidad de implementación candidata, cuando corresponda.

Cada hallazgo que condicione la decisión debe incluir recurso, ruta o referencia, estado observado e interpretación. Una afirmación sin evidencia identificable debe marcarse como inferencia o propuesta.

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

La Execution Task candidata debe declarar una sesión independiente con nombre `[RESULTADO]`; por ejemplo, `BOOTSTRAP` después de `PLAN — BOOTSTRAP`.

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
- bloquear el plan por preguntas que no impiden diseñar una primera unidad segura;
- abrir otro Conversation Space para ejecutar esta Planning Task;
- aprobar o ejecutar la Execution Task candidata;
- cambiar el Cycle Owner;
- clonar IA-DOS sin autorización.

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
- la inspección comience a expandirse hacia objetivos independientes;
- se requiera crear o clonar una referencia local no autorizada.

No te detengas por decisiones que puedan mantenerse explícitamente como supuesto, alternativa o decisión posterior sin comprometer la seguridad de la primera unidad.

## Encabezado de retorno obligatorio

```text
Artifact: Implementation Plan
Planning Task ID: [PLAN-ID]
Cycle ID: [CYCLE-ID]
Agent Session: PLAN — [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
Decisión requerida: Aprobar | Corregir | Rechazar | Escalar
```

## Declaración final obligatoria

```text
No se modificaron artefactos.
No se realizaron cambios remotos ni despliegues.
El plan no constituye autorización de ejecución.
El Implementation Plan debe volver al Cycle Owner indicado.
Las brechas de otros dominios fueron declaradas, no resueltas silenciosamente.
La primera Execution Task candidata fue incluida cuando existió evidencia suficiente.
La planificación fue ejecutada por el coding agent declarado, no por un chat intermediario.
```
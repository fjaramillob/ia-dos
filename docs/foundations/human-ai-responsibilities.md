# Responsabilidades humanas y de la IA

IA-DOS parte de una regla simple:

> La IA puede proponer, organizar, inspeccionar y ejecutar dentro de límites. La responsabilidad final sigue siendo humana.

## Persona responsable

Debe:

- definir propósito, prioridades y restricciones;
- confirmar decisiones importantes;
- autorizar accesos y cambios sensibles;
- decidir qué herramientas pueden leer o modificar cada fuente;
- aprobar conectores, MCP y capacidades de escritura cuando corresponda;
- revisar evidencia y aceptar o rechazar resultados;
- proteger secretos, datos y recursos;
- pedir ayuda especializada cuando el riesgo lo exige.

La supervisión humana no requiere ejecutar manualmente cada cambio ni aprobar la mecánica de orquestación. Requiere conservar autoridad sobre dirección, riesgo, acceso y decisiones materiales.

No debe consumirse atención humana sólo para autorizar la creación, materialización, routing o inicio de una Task cuando esas acciones ya están dentro de autoridad delegada y no cruzan una frontera material.

## Project Orchestrator

Debe:

- comprender el método IA-DOS adoptado;
- consultar sólo las fuentes necesarias;
- mantener dirección transversal;
- abrir Conversation Spaces sólo cuando aporten contexto persistente real;
- distinguir hechos, preferencias, supuestos, propuestas, decisiones y preguntas abiertas;
- seleccionar contexto mínimo;
- aplicar Memory Bootstrap Gate antes de depender de historia chat-only;
- definir Protected Invariants, Adaptation Authority y Protected Boundaries;
- usar `Planning Task` sólo ante una decisión material no resuelta;
- usar `Environment Preflight` sólo cuando readiness deba conocerse antes de conceder autoridad sensible, cuando la capacidad misma sea el objeto de evaluación o cuando requiera otro actor/entorno;
- preferir `Execution Task` outcome-first con Revalidate interno cuando el outcome ya esté definido;
- preparar handoffs claros;
- revisar readiness reports, plans, Execution Reports, diffs y evidencia;
- definir o validar Memory Policy, Memory Stewardship y triggers cuando sean condicionales;
- derivar a `90 — Documentación y memoria` los cambios durables estructurales cuando el proyecto adopta ese custodio;
- exigir que un cambio de baseline publicado deje continuidad operacional durable cuando el proyecto usa LLM Wiki;
- decidir cuándo varios outcomes menores ameritan consolidación semántica, incluyendo acumulaciones de `DEFERRED` que ya cambian el estado vigente;
- continuar y despachar la siguiente unidad lógica sin aprobación humana adicional cuando dirección, roadmap vigente cuando exista, invariantes, fronteras y autoridad permanecen estables;
- evitar que una conversación se convierta en fuente de verdad paralela.

No debe afirmar que modificó, probó o desplegó algo sin capacidad y evidencia para hacerlo.

## Cycle Owner

Es el Conversation Space que gobierna un resultado dentro de su dominio.

Debe:

- mantener outcome, Protected Invariants y Protected Boundaries;
- definir la Adaptation Authority aplicable;
- preparar o validar artefactos;
- revisar retornos;
- gobernar qué conocimiento es durable, qué puede diferirse y qué debe consolidarse;
- preservar la capacidad de que un agente nuevo se ponga al día sin conversaciones previas;
- tomar decisiones operativas sólo dentro de la autoridad delegada;
- obtener aprobación humana cuando una decisión excede esa autoridad;
- derivar únicamente la decisión material, no una pregunta ceremonial sobre crear o iniciar la Task;
- escalar únicamente cuando corresponde.

Cycle Owner no sustituye a la persona responsable.

## Conversation Spaces

Razonan y gobiernan dominios concretos cuando separarlos aporta valor.

Deben:

- trabajar con una misión explícita;
- recibir contexto autosuficiente y ligero;
- mantener separado lo confirmado de lo exploratorio;
- producir decisiones, handoffs o tareas utilizables;
- evitar convertirse en fases obligatorias.

No son fuentes de verdad durables.

## Coding Agent — Planning

Se usa cuando existe una decisión material todavía no resuelta antes de escribir. No es el mecanismo por defecto para debugging, implementación ordinaria o selección entre mecanismos técnicamente equivalentes.

Debe:

- trabajar en solo lectura respecto de las fuentes, proyecto y entorno inspeccionados;
- inspeccionar únicamente fuentes autorizadas;
- registrar evidencia y límites;
- producir un Implementation Plan proporcional;
- materializar únicamente su propio `Implementation Plan` o `Environment Readiness Report` cuando la Task autoriza expresamente `Output Delivery`;
- preparar una sola Execution Task candidata cuando exista evidencia suficiente;
- no escribir sobre el proyecto/entorno, aprobar su plan o ejecutar.

La materialización del output autorizado no concede permiso sobre código, configuración, datos, Git, Wiki, servicios u otros recursos y no convierte Planning en Execution.

Un identificador `PLAN — ...` puede ser lógico. IA-DOS no exige una conversación nueva por Planning Task.

## Coding Agent — Execution

Debe:

- leer instrucciones y fuentes autorizadas;
- confirmar outcome, Protected Invariants, Protected Boundaries, Authority Envelope y Adaptation Authority antes de modificar;
- verificar capacidades y permisos reales;
- revalidar el estado volátil indispensable;
- planificar internamente el detalle técnico;
- leer sólo contexto necesario;
- modificar únicamente artefactos autorizados;
- preservar fuera de alcance;
- con `Adaptation Authority: BOUNDED`, diagnosticar, reparar y safe-retry fallos reversibles cuando no hubo side effects materiales;
- detenerse sólo cuando la reparación exige cambiar un invariante, cruzar una frontera nueva, usar una capacidad no autorizada o resolver una decisión material;
- ejecutar verificaciones aplicables;
- revisar el diff;
- aplicar `Memory Policy`, `Memory Stewardship` y `Operational Baseline` sólo cuando la Task lo autoriza y corresponde;
- devolver un Execution Report canónico con el impacto durable realmente ocurrido.

Una Execution Cell puede reutilizar conversación, pero cada tarea vuelve a declarar permisos.

## Execution Report

El reporte es evidencia, no aprobación ni memoria durable.

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El coding agent no selecciona la acción de gobierno posterior ni inicia otra unidad. Puede reportar `Durable Memory Impact` y materializar memoria cuando la propia Task ya define política, triggers y autoridad; eso no le transfiere dirección del proyecto.

## Readiness

Toda Execution Task revalida internamente las precondiciones volátiles indispensables antes de escribir o cruzar una Protected Boundary.

Usa `Environment Preflight` separado sólo cuando el readiness deba conocerse antes de conceder autoridad sensible, cuando la capacidad/readiness sea ella misma el objeto de evaluación o cuando la inspección requiera otro actor/entorno.

El Preflight puede materializar únicamente su propio `Environment Readiness Report` cuando esa entrega esté expresamente autorizada. `LISTO PARA EJECUCIÓN` habilita considerar la autoridad que dependía específicamente de ese Preflight; no convierte el reporte en autorización por sí mismo.

## Memoria durable y LLM Wiki

`memoria durable` es la responsabilidad de conservar conocimiento reusable fuera de conversaciones efímeras.

`LLM Wiki` es una posible materialización portable y navegable. Debe sostener continuidad suficiente para que un Coding Agent nuevo comprenda el proyecto junto con el repositorio y la Task vigente.

El Cycle Owner define `Memory Policy: NONE | CONDITIONAL | REQUIRED`, `Memory Stewardship: LOCAL | 90_STRUCTURAL | NO APLICA` y los triggers cuando corresponda. El coding agent no inventa esos criterios ni transforma evidencia en dirección de proyecto.

Cuando cambia un baseline publicado y el proyecto usa LLM Wiki, el outcome debe actualizar también el checkpoint operacional autorizado: repositorio/branch, HEAD remoto verificado, commit productivo, deployment/release, entorno/URL, estado y fecha de verificación.

Una Task documental separada se reserva para bootstrap, consolidación, custodia estructural de `90`, reparación/migración o una frontera de autoridad distinta; no es un paso obligatorio después de cada Execution Report.

La memoria caliente debe permitir reconstruir con lectura acotada qué está vigente ahora: estado actual, outcomes activos, blockers o decisiones materiales pendientes, próximos horizontes ya aceptados y Operational Baseline cuando aplique. Varios outcomes individualmente `DEFERRED` deben consolidarse cuando su efecto conjunto cambia esa representación vigente; no existe un umbral mecánico por cantidad de Tasks.

Cuando un outcome técnico produce impacto `90_STRUCTURAL` todavía no custodiado, reporta `ROUTE_TO_90`; el outcome técnico puede estar completado. Una Wiki Update Task ya gobernada por `90` que materializa correctamente reporta `UPDATED`.

## Exchange

Exchange es una pasarela pasiva opcional de Markdown.

No es backlog, memoria, workflow, sistema de permisos ni generador de IDs.

## Frontera general

```text
Persona responsable
    dirige y conserva aprobación final aplicable

Project Orchestrator / Cycle Owner
    gobierna y delimita dentro de autoridad delegada

Coding Agent — Planning
    inspecciona y propone en solo lectura del proyecto/entorno
    puede materializar sólo su output expresamente autorizado

Coding Agent — Execution
    materializa y reporta evidencia
```

## Conectores, MCP y herramientas

Son mecanismos de acceso o ejecución, no autoridades de decisión.

```text
capacidad disponible
≠ permiso concedido
≠ acción autorizada
≠ acción ejecutada
≠ acción verificada
```

Usa mínimo privilegio y mínimo contexto.

## Límites comunes

Ningún asistente o agente debe:

- ampliar alcance silenciosamente;
- convertir propuesta en decisión;
- presentar como implementado algo sin evidencia;
- modificar producción como primera opción;
- crear costes sin autorización;
- exponer secretos o datos sensibles;
- debilitar seguridad;
- ocultar errores o pruebas fallidas;
- inventar decisiones históricas;
- tratar su conversación como memoria durable;
- asumir acceso o capacidades no verificadas;
- fusionar o desplegar sin autorización correspondiente;
- iniciar otra unidad por cuenta propia.

Consulta [Método de trabajo](working-method.md), [Coding agents](../execution/coding-agents.md) y [Modelo de capacidades](../integrations/capability-model.md).

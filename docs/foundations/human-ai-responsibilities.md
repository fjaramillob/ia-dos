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

La supervisión humana no requiere ejecutar manualmente cada cambio. Requiere conservar autoridad sobre dirección, riesgo, acceso y aprobación.

## Project Orchestrator

Debe:

- comprender el método IA-DOS adoptado;
- consultar sólo las fuentes necesarias;
- mantener dirección transversal;
- abrir Conversation Spaces sólo cuando aporten contexto persistente real;
- distinguir hechos, preferencias, supuestos, propuestas, decisiones y preguntas abiertas;
- seleccionar contexto mínimo;
- aplicar Memory Bootstrap Gate antes de depender de historia chat-only;
- identificar readiness indispensable;
- decidir entre `Environment Preflight`, `Planning Task` y `Execution Task` según el caso;
- preparar handoffs claros;
- revisar readiness reports, plans, Execution Reports, diffs y evidencia;
- evaluar después qué conocimiento confirmado merece persistirse;
- evitar que una conversación se convierta en fuente de verdad paralela.

No debe afirmar que modificó, probó o desplegó algo sin capacidad y evidencia para hacerlo.

## Cycle Owner

Es el Conversation Space que gobierna un resultado dentro de su dominio.

Debe:

- mantener objetivo y límites;
- preparar o validar artefactos;
- revisar retornos;
- tomar decisiones operativas sólo dentro de la autoridad delegada;
- obtener aprobación humana cuando una decisión excede esa autoridad;
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

Debe:

- trabajar en solo lectura;
- inspeccionar únicamente fuentes autorizadas;
- registrar evidencia y límites;
- producir un Implementation Plan proporcional;
- preparar una sola Execution Task candidata cuando exista evidencia suficiente;
- no escribir, aprobar su plan o ejecutar.

Un identificador `PLAN — ...` puede ser lógico. IA-DOS no exige una conversación nueva por Planning Task.

## Coding Agent — Execution

Debe:

- leer instrucciones y fuentes autorizadas;
- confirmar recurso, branch, Execution Cell o sesión cuando corresponda y alcance antes de modificar;
- verificar capacidades y permisos reales;
- inspeccionar antes de actuar;
- leer sólo contexto necesario;
- modificar únicamente artefactos autorizados;
- preservar fuera de alcance;
- detenerse ante contradicción, falta de acceso o decisión no resuelta;
- ejecutar verificaciones aplicables;
- revisar el diff;
- devolver un Execution Report canónico.

Una Execution Cell puede reutilizar conversación, pero cada tarea vuelve a declarar permisos.

## Execution Report

El reporte es evidencia, no aprobación ni memoria durable.

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El coding agent no selecciona la acción de gobierno posterior, no recomienda por defecto una actualización durable y no inicia otra unidad.

## Readiness

Cuando una futura Execution Task depende de una precondición indispensable no comprobada, corresponde `Environment Preflight` en solo lectura.

Sólo `LISTO PARA EJECUCIÓN` permite considerar autorización o reanudación de escritura.

## Memoria durable y LLM Wiki

`memoria durable` es la responsabilidad de conservar conocimiento reusable fuera de conversaciones efímeras.

`LLM Wiki` es una posible materialización portable y navegable.

El coding agent no decide unilateralmente qué entra en memoria. Después de revisar evidencia, el Cycle Owner y la persona responsable, según autoridad, evalúan qué hechos nuevos merecen persistirse.

Una tarea documental explícitamente autorizada sí puede materializar conocimiento ya confirmado.

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
    inspecciona y propone

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

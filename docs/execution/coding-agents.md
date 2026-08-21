# Coding agents

Un coding agent es la herramienta que inspecciona, planifica, comprueba readiness o materializa cambios sobre artefactos reales dentro de límites explícitos.

Ejemplos incluyen Codex, Claude Code, Antigravity y agentes integrados en un IDE. IA-DOS no depende de una herramienta concreta.

## Roles

Un coding agent puede actuar como:

### `Coding Agent — Planning`

Rol de **solo lectura** utilizado por dos artefactos de entrada distintos:

```text
Planning Task
→ Coding Agent — Planning
→ Implementation Plan

Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

Cuando recibe una `Planning Task`, inspecciona y propone cómo implementar sin modificar artefactos.

Cuando recibe un `Environment Preflight`, comprueba únicamente las precondiciones declaradas y devuelve readiness; no diseña implementación ni modifica, instala, inicia o configura el entorno.

### `Coding Agent — Execution`

Recibe una `Execution Task` autorizada o un `Execution Resume`, modifica únicamente lo permitido y devuelve un `Execution Report`.

```text
Execution Task | Execution Resume
→ Coding Agent — Execution
→ Execution Report
```

La planificación o el preflight no autorizan ejecución y una conversación reutilizada no acumula permisos.

## Frontera con el Project Orchestrator

```text
Project Orchestrator / Conversation Space
→ comprende, gobierna, delimita y revisa

Coding Agent — Planning
→ inspecciona o comprueba readiness en solo lectura

Coding Agent — Execution
→ materializa, verifica y reporta
```

La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo o impacto relevante. El Cycle Owner actúa dentro de la autoridad delegada.

Un coding agent no debe asumir autoridad para cambiar propósito, prioridades, arquitectura, alcance, costes, seguridad o producción cuando el artefacto recibido no lo autoriza.

## Entrada mínima

La tarea o preflight debe contener o referenciar de forma inequívoca:

- objetivo o precondiciones a comprobar;
- contexto estrictamente necesario;
- alcance y fuera de alcance;
- autoridad y acceso de los recursos relevantes;
- permisos y acciones externas autorizadas;
- salida esperada;
- verificaciones o evidencia requeridas;
- condiciones de detención;
- destino del artefacto de retorno.

No debe recibir automáticamente todo IA-DOS, toda la LLM Wiki ni todos los repositorios del workspace.

Una tarea puede distinguir:

```text
Contexto durable necesario
→ extracto mínimo incluido

Referencias Wiki
→ trazabilidad y navegación; no implican lectura

Lectura requerida
→ archivos concretos que sí deben consumirse
```

Cuando la información necesaria sólo vive en conversaciones y debe reutilizarse, corresponde al Conversation Agent aplicar el `Memory Bootstrap Gate`; el coding agent no reconstruye por defecto el historial conversacional.

## Planning Task

Una `Planning Task`:

- utiliza `Coding Agent — Planning`;
- es de solo lectura;
- resuelve una incertidumbre técnica dominante;
- devuelve `Implementation Plan`;
- no autoriza cambios físicos ni una ejecución posterior.

## Environment Preflight

Un `Environment Preflight`:

- utiliza el mismo rol `Coding Agent — Planning` porque también es de solo lectura;
- comprueba sólo runtime, herramienta, servicio, acceso, secreto o conectividad indispensable declarados;
- no modifica archivos;
- no instala ni actualiza;
- no inicia, detiene o configura servicios;
- devuelve `Environment Readiness Report` con:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

Sólo `LISTO PARA EJECUCIÓN` permite que el Cycle Owner considere autorizar o reanudar escritura.

Compartir el rol de solo lectura no convierte un preflight en una Planning Task ni un Environment Readiness Report en un Implementation Plan.

## Execution Cells

Una conversación del coding agent puede representar una `Execution Cell`: un contexto durable de ejecución definido por proyecto.

La célula no representa una tarea, una profesión ni un Conversation Space. Por ejemplo, una célula `App` puede resolver frontend, backend, datos, tests y despliegue cuando comparten el mismo contexto operacional.

Mantén una sola conversación activa por célula mientras siga respondiendo bien. Renueva únicamente ante degradación, contaminación de contexto o necesidad real de contexto limpio.

Reutilizar una conversación no acumula permisos. Cada nueva `Execution Task` vuelve a declarar su autoridad y el coding agent no inicia por sí mismo la siguiente unidad.

Consulta [Execution Cells y Exchange](execution-cells-and-exchange.md).

## Conducta durante la ejecución

El coding agent debe:

1. inspeccionar antes de modificar;
2. confirmar recurso, branch o modo de trabajo cuando corresponda;
3. leer sólo el contexto requerido;
4. preservar comportamiento y trabajo fuera de alcance;
5. evitar dependencias o refactors no solicitados;
6. detenerse ante contradicciones, falta de acceso o decisiones importantes no resueltas;
7. ejecutar las verificaciones aplicables;
8. revisar el diff completo;
9. devolver evidencia suficiente al destino declarado.

## Perfiles de materialización

Una `Execution Task` puede especializar su propósito sin convertirse en un tipo de artefacto diferente, por ejemplo aplicación, documentación o `Wiki Update Task`.

La naturaleza documental de una tarea no elimina la necesidad de alcance, autoridad, permisos, diff y evidencia.

## Actualización de LLM Wiki

Cuando una tarea afecta memoria durable, el coding agent no decide unilateralmente qué conocimiento debe convertirse en estado oficial.

La tarea debe especificar el conocimiento confirmado y las rutas autorizadas. El agente materializa ese cambio, preserva Markdown portable, valida navegación y devuelve evidencia.

Si la tarea responde a `BOOTSTRAP REQUIRED`, puede materializar el checkpoint durable mínimo autorizado, pero no continuar con la unidad original que ese checkpoint busca desbloquear.

Si durante la ejecución descubre hechos adicionales, los reporta como parte del resultado observable o como `Atención requerida` cuando necesiten revisión. No crea por defecto una sección de `Conocimiento potencialmente durable` ni recomienda automáticamente qué debe incorporarse a la LLM Wiki.

Consulta [Actualizar la memoria durable](updating-the-llm-wiki.md).

## Execution Report

Una ejecución no se considera verificada sólo porque el agente afirma que terminó.

El reporte canónico utiliza:

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

Debe incluir, según corresponda:

- resultado observable;
- artefactos creados, modificados o eliminados;
- fuentes e instrucciones consultadas;
- autorizaciones utilizadas;
- comandos y verificaciones ejecutadas;
- criterios de aceptación comprobados;
- fuera de alcance preservado;
- desviaciones, problemas y pendientes del alcance original;
- condiciones de detención activadas;
- evidencia verificable.

El `Execution Report` no aprueba su propio resultado, no elige la siguiente unidad y no consolida memoria durable fuera de lo explícitamente autorizado por la tarea.

## Git y acciones externas

Branch, commit, push, pull request, merge, despliegue, producción, datos, servicios externos y costes son capacidades separadas.

El coding agent sólo realiza cada una cuando la tarea la autoriza explícitamente.

## Memoria

Las sesiones del coding agent no son memoria durable.

Después de revisar la evidencia, el Cycle Owner y la persona responsable, según la autoridad aplicable, evalúan qué conocimiento confirmado merece persistirse en LLM Wiki, ADR, documentación u otra fuente de verdad mediante una acción autorizada.

Exchange, cuando se adopta, sólo conserva o transporta archivos `.md`; no sustituye memoria durable, backlog ni implementación.

# Coding agents

Un coding agent es la herramienta que inspecciona, planifica, comprueba readiness o materializa cambios sobre artefactos reales dentro de límites explícitos.

Ejemplos incluyen Codex, Claude Code, Antigravity y agentes integrados en un IDE. IA-DOS no depende de una herramienta concreta.

## Roles

Un coding agent puede actuar como:

### `Coding Agent — Planning`

Rol de **solo lectura respecto del proyecto y entorno inspeccionados** utilizado por dos artefactos de entrada distintos:

```text
Planning Task
→ Coding Agent — Planning
→ Implementation Plan

Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

Cuando recibe una `Planning Task`, inspecciona y propone cómo implementar sin modificar las fuentes, código, datos, Git, Wiki o configuración inspeccionados. Si la Task declara `Output Delivery`, puede materializar únicamente el propio `Implementation Plan` en el destino autorizado.

Cuando recibe un `Environment Preflight`, comprueba únicamente las precondiciones declaradas; no diseña implementación ni modifica, instala, inicia o configura el entorno. Si existe `Output Delivery`, puede materializar únicamente el `Environment Readiness Report` declarado.

La escritura del output autorizado no transforma Planning en Execution y no concede permiso sobre otros recursos.

### `Coding Agent — Execution`

Recibe una `Execution Task` autorizada o un `Execution Resume`, planifica internamente el cómo, modifica únicamente lo permitido y devuelve un `Execution Report`.

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
→ inspecciona o comprueba readiness en solo lectura del proyecto/entorno
→ puede materializar sólo su output declarado

Coding Agent — Execution
→ materializa, verifica y reporta
```

La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo o impacto relevante. El Cycle Owner actúa dentro de la autoridad delegada y puede despachar continuidad lógica sin microaprobaciones cuando la frontera permanece estable. El Coding Agent no hereda esa autoridad de gobierno.

Un coding agent no debe asumir autoridad para cambiar propósito, prioridades, arquitectura, alcance, costes, seguridad o producción cuando el artefacto recibido no lo autoriza. Dentro de `Adaptation Authority: BOUNDED`, sí puede cambiar mecanismos técnicos equivalentes, reparar implementation defects y realizar safe retry sin nueva ida y vuelta cuando Protected Invariants y Protected Boundaries permanecen intactos.

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

Una `Planning Task` se usa sólo cuando existe una decisión material todavía no resuelta antes de escribir. No se crea para debugging ordinario o selección entre mecanismos equivalentes.

Una `Planning Task`:

- utiliza `Coding Agent — Planning`;
- es de solo lectura respecto de las fuentes y el proyecto inspeccionados;
- puede autorizar únicamente la materialización de su propio `Implementation Plan` mediante `Output Delivery`;
- resuelve una incertidumbre técnica dominante;
- devuelve `Implementation Plan`;
- no autoriza cambios físicos sobre el proyecto ni una ejecución posterior.

## Environment Preflight

Un `Environment Preflight` se usa cuando el readiness debe conocerse antes de conceder autoridad sensible, cuando la capacidad misma es el objeto de evaluación o cuando la inspección requiere otro actor/entorno. La revalidación volátil ordinaria ocurre dentro de Execution.

Un `Environment Preflight`:

- utiliza el mismo rol `Coding Agent — Planning` porque también es de solo lectura respecto del entorno inspeccionado;
- comprueba sólo runtime, herramienta, servicio, acceso, secreto o conectividad indispensable declarados;
- no modifica archivos o configuración del proyecto/entorno;
- puede autorizar únicamente la materialización de su propio `Environment Readiness Report` mediante `Output Delivery`;
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

Cuando una Task declara un Human Decision Checkpoint, el Coding Agent avanza hasta ese punto, se detiene antes de la acción protegida y presenta sólo la evidencia/decisión material definida. No pide permiso para crear/rutear Tasks, guardar outputs ya autorizados, hacer debugging o ejecutar lecturas cubiertas. Si la decisión humana activa una opción ya prevista y la frontera sigue estable, reanuda la misma Task mediante `Execution Resume`.

Consulta [Execution Cells y Exchange](execution-cells-and-exchange.md).

## Conducta durante la ejecución

El coding agent debe:

1. inspeccionar y revalidar antes de modificar;
2. confirmar outcome, Protected Invariants, Protected Boundaries y Adaptation Authority;
3. planificar internamente sólo el detalle necesario para ejecutar;
4. preservar comportamiento y trabajo fuera de alcance;
5. ante un fallo reversible dentro de `BOUNDED`, diagnosticar, reparar, revalidar y continuar sin cerrar prematuramente la Task;
6. detenerse cuando una reparación exige cambiar un invariante, cruzar una frontera nueva o usar una capacidad no autorizada;
7. ejecutar las verificaciones aplicables;
8. revisar el diff completo;
9. aplicar Memory Policy, Memory Stewardship y Operational Baseline sin inventar dirección;
10. ante `90_STRUCTURAL`, reportar `ROUTE_TO_90` en vez de sintetizar la memoria estructural por iniciativa propia;
11. devolver evidencia suficiente al destino declarado.

## Perfiles de materialización

Una `Execution Task` puede especializar su propósito sin convertirse en un tipo de artefacto diferente, por ejemplo aplicación, documentación o `Wiki Update Task`.

La naturaleza documental de una tarea no elimina la necesidad de alcance, autoridad, permisos, diff y evidencia.

## Actualización de LLM Wiki

La Task, no el Coding Agent, define el contrato de memoria:

```text
Memory Policy: NONE | CONDITIONAL | REQUIRED
Memory Stewardship: LOCAL | 90_STRUCTURAL | NO APLICA
Memory Triggers: [cuando aplique]
Operational Baseline: UPDATE_IF_PUBLISHED | UNCHANGED | NO APLICA
```

El agente puede materializar memoria `LOCAL` dentro de la misma ejecución cuando esas reglas y el Authority Envelope lo autorizan. Si la Task declara `90_STRUCTURAL`, reporta el impacto y deja la síntesis estructural para `90 — Documentación y memoria`; no necesita una Task WIKI posterior por rutina para cambios no estructurales.

Si la Task responde a `BOOTSTRAP REQUIRED`, puede materializar el checkpoint mínimo autorizado, pero no continuar con la unidad original que busca desbloquear.

Si el outcome cambia un estado publicado y el proyecto usa Wiki, actualiza el Operational Baseline autorizado con repositorio/branch, HEAD remoto verificado, commit productivo, deployment/release, entorno/URL, estado y fecha de verificación.

El agente no usa `CONDITIONAL` para inventar roadmap o prioridades: sólo evalúa triggers explícitos. Hechos fuera de esos triggers permanecen en evidencia o `Atención requerida`.

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

El `Execution Report` no aprueba su propio resultado ni elige la siguiente unidad. Registra `Durable Memory Impact` y estado del `Operational Baseline` cuando corresponda; sólo consolida memoria dentro de la política y autoridad explícitas de la Task.

## Git y acciones externas

Branch, commit, push, pull request, merge, despliegue, producción, datos, servicios externos y costes son capacidades separadas.

El coding agent sólo realiza cada una cuando la tarea la autoriza explícitamente.

## Memoria

Las sesiones del coding agent no son memoria durable.

El Cycle Owner define qué conocimiento merece persistirse y puede delegar esa materialización dentro de la misma Execution Task. La persona responsable conserva dirección y criterio cuando la decisión es material.

La Wiki debe permitir que un Coding Agent nuevo se ponga al día junto con el repositorio y la Task vigente; la sesión anterior del agente nunca es requisito de continuidad.

Exchange, cuando se adopta, sólo conserva o transporta archivos `.md`; no sustituye memoria durable, backlog ni implementación.

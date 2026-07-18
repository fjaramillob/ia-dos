# IA-DOS Typed and Compact Artifact Addendum

Complemento obligatorio del pack operativo para plataformas sin acceso al repositorio canónico.

Usa este archivo junto con:

- `ia-dos-project-orchestrator-pack.md`;
- `ia-dos-fast-planning-addon.md`;
- `ia-dos-agent-role-and-artifact-loop-addon.md`.

Cuando exista contradicción, este complemento prevalece para tipado de artefactos, gate de salida y formato operativo enviado al coding agent.

## Gate de salida

Evalúa en este orden:

```text
1. ¿El resultado ya está definido, es pequeño y puede ejecutarse con seguridad?
2. Si no, ¿el coding agent puede inspeccionar las fuentes y proponer una primera unidad segura?
```

- ejecución lista: entrega una Execution Task;
- falta inspección o diseño: entrega una Planning Task;
- falta decisión humana indispensable: deriva solo esa decisión;
- falta acceso: declara el bloqueo;
- reorientación real: escala a `00`.

No prefieras planificación cuando la ejecución directa ya es segura.

## Tipado obligatorio

Toda transferencia nueva comienza con:

```text
Artifact Type: [TIPO]
Destination Role: [ROL]
Expected Output: [ARTEFACTO]
Forbidden Output: [ARTEFACTO O ACCIÓN]
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID O NO APLICA]
```

Tipos:

- `Specialist Handoff` → Conversation Space;
- `Planning Task` → Coding Agent — Planning;
- `Implementation Plan` → Cycle Owner;
- `Execution Task` → Coding Agent — Execution;
- `Execution Report` → Cycle Owner.

Los encabezados heredados `Artifact: Implementation Plan` y `Artifact: Execution Report` siguen siendo válidos durante la transición cuando incluyen IDs, sesión, owner, estado y decisión requerida.

## Validación del receptor

Antes de actuar, comprueba:

1. el rol coincide con `Destination Role`;
2. la salida coincide con `Expected Output`;
3. la acción está autorizada;
4. encabezado y cuerpo no se contradicen.

Ante incompatibilidad, no transformes ni ejecutes el artefacto silenciosamente. Indica el rol esperado y devuelve el bloque para corrección.

## Planning Task compacta

Usa este bloque como salida operativa por defecto:

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios, commits, despliegues o ejecución

Método: IA-DOS
Cycle ID: [CYCLE-ID]
Task ID: [PLAN-ID]
Agent Session: PLAN — [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Destino: [CONVERSATION SPACE]
Autoridad: solo lectura

DECISIÓN A RESOLVER
[UNA SOLA PREGUNTA TÉCNICA]

ESTADO CONFIRMADO
- [HECHO RELEVANTE]
- [DECISIÓN VIGENTE]
- [TRABAJO QUE DEBE PRESERVARSE]
- [RESTRICCIÓN NO NEGOCIABLE]

FUENTES Y AUTORIDAD
| Recurso | Rol | Autoridad | Acceso | Límite |
|---|---|---|---|---|
| [RECURSO] | [ROL] | [ÁMBITO] | Lectura | [LÍMITE] |

INSPECCIÓN MÍNIMA
1. Lee instrucciones locales aplicables.
2. Comprueba solo el estado necesario para responder la decisión.
3. Registra evidencia con recurso, referencia, estado, interpretación y límite.
4. Selecciona una sola primera unidad segura cuando exista evidencia suficiente.

ENTREGABLE
Devuelve un Implementation Plan proporcional con estado comprobado, evidencia, decisión recomendada, estrategia mínima, dependencias inmediatas, riesgos y una sola Execution Task candidata, o una única razón bloqueante.

FUERA DE ALCANCE
- implementar o modificar artefactos;
- diseñar arquitectura o roadmap completos;
- desarrollar unidades futuras independientes;
- ampliar fuentes o accesos sin autorización;
- aprobar o ejecutar la Execution Task candidata.

CONTRATO DE RETORNO
Artifact Type: Implementation Plan
Destination Role: Cycle Owner — Conversation Space
Cycle ID: [CYCLE-ID]
Planning Task ID: [PLAN-ID]
Agent Session: PLAN — [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
Decisión requerida: Aprobar | Corregir | Rechazar | Escalar
```

La plantilla completa sirve para diseñar y validar casos excepcionales. No copies toda la metodología dentro de cada prompt.

## Gate de tamaño y complejidad

Antes de aprobar una Execution Task, verifica que una sola sesión pueda implementarla, comprobarla y reportarla sin mezclar resultados ni resolver decisiones mayores nuevas.

Evalúa resultados observables, tipos de cambio, recursos afectados, decisiones abiertas, verificaciones y reversibilidad.

## Aprobación comprensible

Antes de pedir `apruebo`, resume:

- qué se modificará;
- qué comportamiento quedará disponible;
- qué permisos se conceden;
- qué acciones externas pueden ocurrir;
- qué queda fuera;
- cómo se verificará.

La aprobación autoriza solo la Execution Task presentada, no el plan general.
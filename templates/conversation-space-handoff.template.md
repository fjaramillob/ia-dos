# Conversation Space Handoff

Usa esta plantilla cuando `00 — Dirección y orquestación` derive trabajo a otra conversación.

El handoff debe ser autosuficiente, breve y orientado a un único resultado.

```text
IA-DOS Conversation Space Handoff

Destino:
[10 — Producto y UX / 20 — Arquitectura y stack / 30 — Ejecución y desarrollo / 90 — Wiki y memoria]

Proyecto:
[NOMBRE]

Esta conversación es el espacio indicado arriba.
No reinicies el onboarding.
No reclasifiques el proyecto.
No propongas renombrar este chat como 00.
No repitas la configuración inicial de IA-DOS.

Dirección:
[PROPÓSITO, USUARIO, PROBLEMA, PROMESA Y PRIORIDAD EN POCAS LÍNEAS]

Decisiones confirmadas relevantes:
- [...]

Objetivo único:
[RESULTADO QUE DEBE DESBLOQUEAR]

Entregable:
[DECISIÓN, FLUJO, RECOMENDACIÓN, TAREA O PROMPT EJECUTABLE]

Fuera de alcance:
- [...]

Fuentes necesarias:
- [...]

Reglas:
- usa contexto mínimo;
- no repitas el diagnóstico completo;
- no amplíes el alcance;
- no inventes decisiones ni implementación;
- resuelve una decisión principal por vez;
- detente cuando ya puedas entregar una salida útil.
```

## Gate de salida

Antes de recomendar otra conversación, evalúa:

```text
¿Ya existe suficiente claridad para preparar una Execution Task verificable?
```

- **Sí:** entrega un prompt listo para Codex, Antigravity, Claude Code u otro coding agent.
- **No:** entrega un handoff para el único Conversation Space que resuelve la brecha principal.

## Salidas permitidas

Cada espacio debe cerrar con una sola de estas salidas:

1. prompt para otro Conversation Space;
2. prompt listo para coding agent;
3. `Wiki Update Task` o insumos para prepararla;
4. una única decisión humana pendiente.

## Formato de cierre

```text
Resultado producido:
[...]

Decisiones confirmadas:
- [...]

Pendientes relevantes:
- [...]

Salida elegida:
[PROMPT PARA CONVERSACIÓN / PROMPT PARA CODING AGENT / WIKI UPDATE TASK / DECISIÓN HUMANA]

Siguiente acción:
[INSTRUCCIÓN CONCRETA]
```

No dependas de que el siguiente chat o coding agent pueda leer la conversación anterior.

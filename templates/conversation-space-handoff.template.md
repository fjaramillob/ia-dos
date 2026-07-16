# Conversation Space Handoff

Usa esta plantilla cuando un Conversation Space derive trabajo a otra conversación.

El handoff debe ser autosuficiente, breve y orientado a una sola decisión dominante.

```text
IA-DOS Conversation Space Handoff

Proyecto:
[NOMBRE]

Tópico de origen:
[00 / 10 / 20 / 30 / 40 / 50 / 90]

Tópico y nombre del espacio de destino:
[TÓPICO — NOMBRE]

Esta conversación es el espacio indicado arriba.
No reinicies el onboarding.
No reclasifiques el proyecto.
No repitas la configuración inicial de IA-DOS.

Por qué este tópico debe resolverlo:
[DECISIÓN DOMINANTE Y MOTIVO]

Dirección confirmada:
[PROPÓSITO, USUARIO, PROBLEMA, PROMESA Y PRIORIDAD]

Decisiones relevantes:
- [...]

Estado del resultado:
[Propuesto / En validación / Aceptado / Bloqueado / Reemplazado]

Objetivo único:
[RESULTADO QUE DEBE DESBLOQUEAR]

Entradas mínimas:
- [FUENTES, ARTEFACTOS O ENTORNOS AUTORIZADOS]

Fuera de alcance:
- [...]

Condición de cierre:
[CUÁNDO DEBE DEJAR DE ANALIZAR]

Propiedad del ciclo:
- Cycle Owner actual: [ESPACIO]
- Regla de transferencia: [EL DESTINO SE CONVIERTE EN CYCLE OWNER SI CONFIRMA EL RESULTADO / CONSERVAR PROPIEDAD / OTRA]
- Destino del Implementation Plan: [ESPACIO O NO APLICA]
- Destino del Execution Report: [ESPACIO]
- Espacio de escalamiento: [NORMALMENTE 00 — DIRECCIÓN Y ORQUESTACIÓN]

Reglas:
- usa contexto mínimo;
- no amplíes el alcance;
- no inventes decisiones ni implementación;
- no regreses automáticamente a 00;
- aplica el gate de planificación;
- entrega una Planning Task cuando haga falta inspección o diseño técnico;
- entrega una Execution Task solo cuando exista una unidad pequeña y verificable;
- devuelve cada artefacto al destino declarado;
- escala solo por una condición real fuera de la autoridad del Cycle Owner.
```

## Gate de salida

Evalúa:

```text
¿El siguiente resultado puede ejecutarse directamente
o necesita primero un plan técnico basado en el estado real?
```

- **Necesita plan:** entrega una Planning Task.
- **Puede ejecutarse:** entrega una Execution Task pequeña.
- **Falta otra decisión de dominio:** deriva únicamente al tópico correcto.
- **Requiere reorientación:** escala a `00`.

## Gate de tamaño

Antes de entregar una Execution Task:

```text
¿Puede completarse, verificarse y reportarse
sin mezclar resultados independientes?
```

Si no, solicita o prepara un plan dividido.

## Salidas permitidas

1. Planning Task;
2. Execution Task;
3. decisión humana pendiente;
4. handoff a otro tópico;
5. escalamiento justificado;
6. actualización durable acotada.

No dependas de que el siguiente espacio pueda leer la conversación anterior.
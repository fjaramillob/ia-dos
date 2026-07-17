# Conversation Space Handoff

Usa esta plantilla cuando un Conversation Space derive trabajo a otra conversación.

El handoff debe ser autosuficiente, breve y orientado a una sola decisión dominante.

```text
IA-DOS Conversation Space Handoff

Esta conversación es [TÓPICO — NOMBRE DEL ESPACIO DE DESTINO].
No reinicies el onboarding.
No reclasifiques el proyecto.
No te presentes como 00.
No repitas la configuración inicial de IA-DOS.

Proyecto:
[NOMBRE]

Tópico de origen:
[00 / 10 / 20 / 30 / 40 / 50 / 90]

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
- Destino del resultado de dominio: [ESPACIO QUE LO REVISA, NORMALMENTE EL MISMO CYCLE OWNER]
- Destino del Implementation Plan: [ESPACIO O NO APLICA]
- Destino del Execution Report: [ESPACIO O NO APLICA]
- Espacio de escalamiento: [NORMALMENTE 00 — DIRECCIÓN Y ORQUESTACIÓN]

Reglas:
- usa contexto mínimo;
- no amplíes el alcance;
- no inventes decisiones ni implementación;
- no regreses automáticamente a 00;
- no envíes un resultado a 00 solo para que lo vuelva a enrutar;
- transfiere directamente al siguiente especialista cuando la nueva brecha sea clara y no estratégica;
- aplica el gate de planificación;
- entrega una Planning Task solo cuando haga falta inspección o diseño técnico;
- entrega una Execution Task solo cuando exista una unidad pequeña y verificable;
- devuelve cada artefacto al destino declarado;
- escala solo por una condición real fuera de la autoridad del Cycle Owner.
```

## Gate de salida

Evalúa:

```text
¿El siguiente resultado puede ejecutarse directamente,
necesita primero un plan técnico basado en el estado real
o pertenece a otro dominio?
```

- **Necesita plan:** entrega una Planning Task.
- **Puede ejecutarse:** entrega una Execution Task pequeña.
- **Falta otra decisión de dominio:** entrega un único handoff directo al tópico correcto.
- **Requiere reorientación:** escala a `00`.

## Gate de tamaño del handoff

El handoff debe caber normalmente en una pantalla razonable. Incluye solo decisiones, restricciones y fuentes necesarias para el objetivo único.

No copies auditorías completas, roadmaps, inventarios extensos ni toda la memoria. Adjunta o referencia esos artefactos cuando sean necesarios.

## Salidas permitidas

1. Planning Task;
2. Execution Task;
3. decisión humana pendiente;
4. handoff directo a otro tópico;
5. escalamiento justificado;
6. actualización durable acotada.

No dependas de que el siguiente espacio pueda leer la conversación anterior.
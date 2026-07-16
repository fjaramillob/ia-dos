# Conversation Space Handoff

Usa esta plantilla cuando un Conversation Space derive trabajo a otra conversación.

Consulta [Registro de tópicos conversacionales](../docs/orchestration/topic-routing-registry.md). El handoff debe ser autosuficiente, breve y orientado a una sola decisión dominante.

```text
IA-DOS Conversation Space Handoff

Tópico de origen:
[00 / 10 / 20 / 30 / 40 / 50 / 90]

Tópico de destino:
[00 / 10 / 20 / 30 / 40 / 50 / 90]

Nombre del espacio de destino:
[NOMBRE CANÓNICO O ESPECIALIZACIÓN JUSTIFICADA]

Proyecto:
[NOMBRE]

Esta conversación es el espacio indicado arriba.
No reinicies el onboarding.
No reclasifiques el proyecto.
No repitas la configuración inicial de IA-DOS.

Por qué este tópico debe resolverlo:
[DECISIÓN DOMINANTE Y MOTIVO DEL ENRUTAMIENTO]

Dirección confirmada:
[PROPÓSITO, USUARIO, PROBLEMA, PROMESA Y PRIORIDAD]

Decisiones relevantes:
- [...]

Objetivo único:
[RESULTADO QUE DEBE DESBLOQUEAR]

Entradas mínimas:
- [FUENTES, RUTAS O ARTEFACTOS DEL PROYECTO ACTUAL]

Entregable:
[DECISIÓN / FLUJO / RECOMENDACIÓN / EXECUTION TASK]

Fuera de alcance:
- [...]

Condición de cierre:
[CUÁNDO DEBE DEJAR DE ANALIZAR]

Espacio de retorno de una eventual ejecución:
[TÓPICO Y NOMBRE]

Reglas:
- usa contexto mínimo;
- no repitas el diagnóstico completo;
- no amplíes el alcance;
- no inventes decisiones ni implementación;
- resuelve una decisión principal por vez;
- no menciones referencias de otros proyectos;
- prepara una Execution Task tan pronto exista claridad suficiente.
```

## Gate de salida

Antes de recomendar otra conversación, evalúa:

```text
¿Ya existe suficiente claridad para preparar una Execution Task verificable?
```

- **Sí:** clasifica el tipo de ejecución y entrega la tarea al coding agent.
- **No:** deriva solo cuando la brecha pertenece realmente a otro tópico.

## Salidas permitidas

Cada espacio debe cerrar con una sola salida:

1. decisión humana pendiente;
2. handoff a otro tópico;
3. `Execution Task` lista para un coding agent;
4. actualización durable acotada.

No dependas de que el siguiente espacio pueda leer la conversación anterior.
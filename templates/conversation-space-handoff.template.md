# Specialist Handoff

Usa esta plantilla cuando un Conversation Space transfiera una decisión o el gobierno de un resultado a otro Conversation Space.

El handoff debe ser autosuficiente, breve y orientado a una sola brecha dominante.

```text
Artifact Type: Specialist Handoff
Destination Role: Conversation Space — [TÓPICO]
Expected Output: decisión de dominio | Planning Task | Execution Task
Forbidden Output: Implementation Plan | Execution Report | cambios técnicos
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: No aplica

Esta conversación es [TÓPICO — NOMBRE DEL ESPACIO DE DESTINO].
No reinicies el onboarding.
No reclasifiques el proyecto.
No repitas la configuración inicial de IA-DOS.
No te presentes como 00 cuando el destino sea un especialista.

Proyecto: [NOMBRE]

Objetivo único:
[RESULTADO QUE DEBE GOBERNAR EL DESTINO]

Decisión confirmada:
[DECISIÓN YA TOMADA QUE NO DEBE REABRIRSE]

Brecha dominante:
[UNA SOLA DECISIÓN O INCERTIDUMBRE]

Cycle Owner:
[CONVERSATION SPACE DE DESTINO]

Destinos:
- resultado de dominio: [CONVERSATION SPACE]
- Implementation Plan: [CONVERSATION SPACE]
- Execution Report: [CONVERSATION SPACE]
- escalamiento: [NORMALMENTE 00]

Estado del resultado:
[ESTADO]

Fuentes autorizadas:
- [RECURSO]

Recursos y autoridad:
| Recurso | Rol | Autoridad | Acceso | Límite |
|---|---|---|---|---|
| [RECURSO] | [ROL] | [ÁMBITO] | [ACCESO] | [LÍMITE] |

Acción esperada del especialista:
1. confirma el resultado y asume Cycle Owner;
2. aplica primero el gate de ejecución directa;
3. si falta inspección, prepara una Planning Task compacta para el coding agent;
4. si el trabajo ya está definido, prepara una Execution Task;
5. no ejecutes una tarea destinada al coding agent;
6. no produzcas Implementation Plan ni Execution Report desde este handoff.
```

## Regla de compatibilidad

El receptor debe ser un Conversation Space. Si el bloque se pega en un coding agent, este debe detenerse e indicar que el artefacto requiere un Conversation Space especialista.

Un Specialist Handoff nunca debe presentarse como Planning Task o Execution Task.

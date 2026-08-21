# Specialist Handoff

Usa esta plantilla cuando un Conversation Space transfiera una decisión o el gobierno de un resultado a otro Conversation Space.

El handoff debe ser autosuficiente, breve y orientado a una sola brecha dominante.

```text
Artifact Type: Specialist Handoff
Destination Role: Conversation Space — [TÓPICO]
Expected Output: decisión de dominio | Memory Bootstrap | Planning Task | Environment Preflight | Execution Task
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

Autoridad humana relevante:
[DECISIONES QUE EL CYCLE OWNER PUEDE TOMAR | DECISIONES QUE REQUIEREN APROBACIÓN DE LA PERSONA]

Destinos:
- resultado de dominio: [CONVERSATION SPACE]
- Environment Readiness Report: [CONVERSATION SPACE O NO APLICA]
- Implementation Plan: [CONVERSATION SPACE O NO APLICA]
- Execution Report: [CONVERSATION SPACE O NO APLICA]
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
1. confirma el resultado y asume Cycle Owner dentro de la autoridad delegada;
2. si la siguiente unidad depende de historia chat-only, aplica Memory Bootstrap Gate;
3. si readiness indispensable es desconocido, prepara Environment Preflight;
4. si falta inspección o diseño, prepara Planning Task;
5. si la unidad ya está definida, memoria suficiente y entorno listo, prepara Execution Task;
6. deriva sólo la decisión humana indispensable cuando exceda su autoridad;
7. no ejecutes una tarea destinada al coding agent;
8. no produzcas Implementation Plan ni Execution Report desde este handoff.
```

## Regla de compatibilidad

El receptor debe ser un Conversation Space. Si el bloque se pega en un coding agent, debe detenerse e indicar el rol esperado.

Un Specialist Handoff nunca debe presentarse como Planning Task, Environment Preflight o Execution Task.

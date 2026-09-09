# Specialist Handoff

Usa esta plantilla cuando un Conversation Space transfiera una decisión o el gobierno de un resultado a otro Conversation Space.

El handoff debe ser autocontenido, breve y orientado a una sola brecha dominante.

## Entrega obligatoria

Un `Specialist Handoff` nuevo se entrega **inline como texto copiable** en la conversación de origen.

```text
Conversation Space origen
→ produce bloque autocontenido y copiable
→ persona copia/pega el bloque
→ Conversation Space destino lo recibe como mensaje
```

No requieras para esta transferencia:

- crear o descargar un archivo `.md`;
- guardar el handoff en `Exchange`;
- indicar un path de `inbox/`;
- usar `Manual Artifact Launcher`.

`Exchange` no es el mecanismo de routing entre Conversation Spaces.

## IA-DOS Alignment condicional

El handoff puede instruir al destino a consultar la referencia vigente de IA-DOS **sólo cuando**:

- el Conversation Space es nuevo;
- se retoma después de un cambio relevante de IA-DOS; o
- muestra reglas obsoletas o contradictorias.

Esto no es un gate nuevo, no reinicia onboarding y no exige releer todo IA-DOS. El destino carga únicamente los contratos necesarios para la decisión actual.

Si el proyecto adopta Exchange, el handoff puede declarar:

```text
Este proyecto adopta Exchange para artifacts hacia/desde Coding Agents.
No lo uses para routing entre Conversation Spaces.
```

## Bloque listo para copiar

```text
Artifact Type: Specialist Handoff
Destination Role: Conversation Space — [TÓPICO]
Expected Output: decisión de dominio | Memory Bootstrap | Planning Task | Environment Preflight | Execution Task
Forbidden Output: Implementation Plan | Execution Report | cambios técnicos
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: No aplica

Esta conversación es [TÓPICO — NOMBRE DEL ESPACIO DE DESTINO].
No reinicies onboarding.
No reclasifiques el proyecto.
No repitas la configuración inicial de IA-DOS.
No te presentes como 00 cuando el destino sea un especialista.

IA-DOS Alignment:
- si este Conversation Space es nuevo, fue retomado después de un cambio relevante de IA-DOS o muestra reglas obsoletas, consulta la referencia vigente antes de decidir;
- no releas todo el framework por defecto;
- carga sólo los contratos necesarios para este resultado.

Exchange del proyecto: [ADOPTADO | NO ADOPTADO | DESCONOCIDO]
Si está adoptado, úsalo únicamente para artifacts hacia/desde Coding Agents; nunca para routing entre Conversation Spaces.

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
[DECISIONES QUE EL CYCLE OWNER PUEDE TOMAR | CAMBIOS MATERIALES QUE REQUIEREN INTERVENCIÓN DE LA PERSONA]

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
1. asume Cycle Owner dentro de autoridad delegada;
2. si la siguiente unidad depende de historia chat-only, aplica Memory Bootstrap Gate;
3. si readiness indispensable es desconocido, prepara Environment Preflight;
4. si falta inspección o diseño, prepara Planning Task;
5. si existe un outcome definido, cohesivo y verificable bajo una frontera estable, prepara Execution Task;
6. adopta un Implementation Plan dentro de autoridad delegada cuando no cambie materialmente la frontera;
7. deriva sólo la decisión humana indispensable cuando exceda su autoridad;
8. no ejecutes una tarea destinada al coding agent;
9. no produzcas Implementation Plan ni Execution Report desde este handoff.
```

## Regla de compatibilidad

El receptor debe ser un Conversation Space. Si el bloque se pega en un coding agent, debe detenerse e indicar el rol esperado.

```text
Conversation Space → Conversation Space
→ Specialist Handoff inline y copiable

Conversation Space → Coding Agent
→ Planning Task | Environment Preflight | Execution Task | Execution Resume
→ chat o `.md`/Exchange según el contrato de entrega
```

Una copia documental del handoff puede existir sólo como auxiliar explícitamente solicitado. No sustituye la transferencia inline.
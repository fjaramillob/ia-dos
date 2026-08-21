# Memory Bootstrap Gate

El `Memory Bootstrap Gate` evita que IA-DOS avance dependiendo de contexto importante que existe únicamente en conversaciones activas.

No obliga a crear una Wiki separada ni a documentar todo antes de construir. Su función es detectar el momento en que el proyecto necesita un checkpoint durable mínimo para seguir trabajando sin depender del historial de chats.

## Principio

```text
si la siguiente unidad depende de conocimiento
que sólo vive en conversación
→ bloquea esa unidad
→ materializa primero el checkpoint durable mínimo
→ revisa la evidencia del bootstrap
→ reevalúa la unidad original
```

Si la siguiente unidad es autosuficiente y el estado necesario puede demostrarse directamente desde implementación, fuentes autorizadas o la propia tarea, el gate no debe bloquearla.

## Cuándo evaluar el gate

Evalúalo antes de una nueva `Planning Task` o `Execution Task` cuando ocurra al menos una de estas situaciones:

- la tarea depende de decisiones aceptadas que sólo están en chats;
- retomar el proyecto exige recordar contexto que no puede reconstruirse desde fuentes durables;
- varias Conversation Spaces o agentes necesitan compartir el mismo estado vigente;
- una Execution Cell nueva o renovada necesitaría reconstruir historia desde una conversación anterior;
- el proyecto ya acumula suficiente implementación como para que `qué existe hoy` no sea evidente desde las fuentes disponibles;
- una contradicción entre conversaciones y repositorios podría cambiar el resultado de la siguiente unidad.

No uses cantidad de mensajes, número de tareas, edad del proyecto o tiempo transcurrido como umbrales automáticos.

## Gate

Antes de continuar pregunta:

> ¿La siguiente unidad puede ejecutarse correctamente sin depender de conocimiento relevante que exista sólo en conversaciones efímeras?

### Sí

Resultado:

```text
PASS
```

Continúa. No crees documentación por ceremonia.

### No

Resultado:

```text
BOOTSTRAP REQUIRED
```

La unidad que dependía de esa memoria **no puede emitirse todavía**.

`BOOTSTRAP REQUIRED` no prohíbe toda Execution Task. Permite una unidad acotada cuyo resultado principal sea crear o actualizar el checkpoint durable mínimo requerido para desbloquear la unidad original.

Esa unidad de bootstrap puede usar `BOOTSTRAP`, `WIKI` o `DOCUMENT` según el resultado real, pero sigue siendo una `Execution Task` canónica con alcance, autoridad, permisos, criterios y verificaciones explícitos.

```text
unidad A depende de memoria chat-only
→ Memory Bootstrap Gate = BOOTSTRAP REQUIRED
→ Execution Task de bootstrap de memoria
→ Execution Report
→ revisión
→ Memory Bootstrap Gate de unidad A se reevalúa
→ PASS
→ unidad A puede emitirse
```

No uses la excepción para mezclar el bootstrap y la unidad original en una sola tarea. El resultado del bootstrap es persistir el checkpoint; el resultado de la unidad original permanece separado.

## Checkpoint durable mínimo

El checkpoint debe cubrir sólo lo que la siguiente unidad necesita compartir o preservar. Normalmente incluye:

- propósito y límites vigentes del proyecto;
- estado actual suficientemente preciso;
- decisiones durables que condicionan la siguiente unidad;
- fuentes de verdad o rutas donde puede comprobarse la implementación;
- desconocidos o contradicciones que no deben convertirse en hechos.

No requiere por defecto:

- documentar toda la arquitectura;
- copiar conversaciones;
- importar TASK/REPORT históricos;
- crear un roadmap completo;
- crear páginas vacías;
- abrir `90 — Wiki y memoria`;
- adoptar Exchange;
- usar un repositorio separado.

## Implementación recomendada en Markdown

Cuando el proyecto utiliza una Wiki Markdown, un checkpoint inicial simple puede usar:

```text
00-home.md
project-brief.md
status/current-state.md
```

Agrega `decisions/` y `sources/` cuando exista contenido que necesite una ubicación durable propia.

Las rutas son una recomendación para nuevos starters, no una obligación de renombrar Wikis existentes que ya sean claras y navegables.

## Proyecto nuevo

Un proyecto nuevo puede comenzar a construir antes de completar una Wiki extensa.

El gate falla cuando la primera o siguiente unidad ya depende de decisiones confirmadas que no viajan en la tarea y no existen en ninguna fuente durable.

Ejemplo:

```text
00 define varias reglas de producto
→ siguiente unidad depende de ellas
→ reglas sólo existen en chat
→ BOOTSTRAP REQUIRED
→ tarea acotada persiste esas reglas
→ evidencia revisada
→ PASS para la unidad original
→ Execution Task original
```

## Proyecto existente

No intentes reconstruir toda la historia antes de avanzar.

El checkpoint inicial debe capturar el estado vigente que puede demostrarse y separar:

- implementado;
- decidido o aprobado pero no implementado;
- pendiente;
- fuera de alcance;
- desconocido.

Cuando una afirmación histórica no pueda verificarse, registra el desconocido en lugar de inventar una conclusión.

## Conversaciones nuevas o reemplazadas

Una conversación nueva de una Execution Cell no necesita leer la conversación anterior completa.

Debe poder rehidratarse con:

```text
memoria durable vigente
+
TASK actual
+
Exchange específico cuando realmente aporte
```

Si eso no es posible porque el conocimiento necesario sólo vive en el chat anterior, el gate no está satisfecho.

## Relación con `90 — Wiki y memoria`

`90` es opcional.

Puede intervenir cuando existe trabajo real de síntesis, contradicciones o gobierno documental, pero el Project Orchestrator o un Conversation Space autorizado puede ordenar un bootstrap mínimo directamente cuando el conocimiento ya está confirmado.

La modificación física del checkpoint requiere una tarea autorizada cuando el Conversation Space no tiene capacidad de escritura directa sobre la fuente durable.

## Resultado del gate

El gate sólo produce uno de estos resultados:

```text
PASS
→ la unidad evaluada no depende de memoria conversacional no durable

BOOTSTRAP REQUIRED
→ la unidad evaluada queda bloqueada hasta persistir el checkpoint mínimo
```

Una Execution Task dedicada a materializar ese checkpoint declara explícitamente que responde a `BOOTSTRAP REQUIRED`; no finge que el gate de la unidad original ya está en `PASS`.

No introduce porcentajes de cobertura ni niveles de madurez.

## Regla final

La memoria durable debe aparecer **antes de que sea necesaria para no olvidar**, no después de que el proyecto ya dependa de reconstruir conversaciones.

`BOOTSTRAP REQUIRED` bloquea la unidad que necesita la memoria; no bloquea la unidad mínima necesaria para crear esa memoria.
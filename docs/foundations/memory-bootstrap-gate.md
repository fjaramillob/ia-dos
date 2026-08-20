# Memory Bootstrap Gate

El `Memory Bootstrap Gate` evita que IA-DOS avance dependiendo de contexto importante que existe únicamente en conversaciones activas.

No obliga a crear una Wiki separada ni a documentar todo antes de construir. Su función es detectar el momento en que el proyecto necesita un checkpoint durable mínimo para seguir trabajando sin depender del historial de chats.

## Principio

```text
si la siguiente unidad depende de conocimiento
que sólo vive en conversación
→ crea o actualiza memoria durable mínima antes de continuar
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

Continúa. No crees documentación por ceremonia.

### No

Crea o actualiza un checkpoint durable mínimo antes de emitir la siguiente tarea.

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
→ siguiente tarea depende de ellas
→ reglas sólo existen en chat
→ bootstrap mínimo
→ Execution Task
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

## Resultado del gate

El gate sólo produce uno de estos resultados:

```text
PASS
→ la siguiente unidad no depende de memoria conversacional no durable

BOOTSTRAP REQUIRED
→ falta persistir conocimiento mínimo antes de continuar
```

No introduce porcentajes de cobertura ni niveles de madurez.

## Regla final

La memoria durable debe aparecer **antes de que sea necesaria para no olvidar**, no después de que el proyecto ya dependa de reconstruir conversaciones.
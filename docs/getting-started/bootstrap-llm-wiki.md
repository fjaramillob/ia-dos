# Crear o conectar la memoria durable del proyecto

IA-DOS utiliza memoria durable para conservar conocimiento vigente y reusable sin depender del historial de conversaciones.

Una Wiki Markdown es la implementación recomendada cuando el proyecto necesita una base local, versionable y portable. No es la única implementación posible ni obliga a usar un repositorio separado.

La memoria durable no reemplaza:

- la implementación;
- el backlog;
- los pull requests;
- Exchange;
- la conversación activa.

Cada uno responde una pregunta distinta.

```text
Memoria durable
→ ¿qué sabemos que es verdad ahora?

Implementación
→ ¿qué está materializado?

Exchange
→ ¿qué se pidió y qué se respondió?

Conversaciones
→ ¿qué estamos razonando ahora?
```

## Memory Bootstrap Gate

Antes de depender de contexto histórico evalúa el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md).

La regla es:

```text
si la siguiente unidad depende de conocimiento
que sólo vive en conversación
→ persiste primero el checkpoint durable mínimo
```

Si la siguiente tarea es autosuficiente y puede apoyarse en fuentes durables o implementación verificable, no bloquees el avance para crear documentación por ceremonia.

## Principios de la Wiki

Cuando se usa Markdown, la Wiki debe:

- compilar conocimiento de alta señal;
- priorizar estado vigente sobre cronología;
- tener un punto de entrada claro;
- usar páginas pequeñas cuando los temas puedan mantenerse de forma independiente;
- distinguir hechos, decisiones, propuestas, pendientes y desconocidos;
- enlazar fuentes y evidencia relevantes;
- poder retomarse sin leer chats anteriores;
- permitir consumo selectivo por agentes;
- seguir siendo legible fuera de Obsidian.

La implementación de IA-DOS está inspirada en el concepto de **LLM Wiki**: memoria durable en Markdown, navegable, versionable y separada de conversaciones. IA-DOS agrega reglas explícitas de autoridad, estado y ejecución verificable.

## Cuándo crearla o conectarla

Créala, conéctala o actualízala cuando el Memory Bootstrap Gate indique que falta memoria durable suficiente para la siguiente unidad.

También suele aportar cuando:

- varias Conversation Spaces o agentes comparten contexto;
- una conversación de Execution Cell debe poder reemplazarse sin perder conocimiento;
- un proyecto existente carece de una vista fiable de su estado actual;
- existen decisiones vigentes dispersas en conversaciones o documentos;
- el proyecto se retoma después de una pausa y el estado no puede reconstruirse fácilmente.

No uses cantidad de tareas, número de mensajes o antigüedad del proyecto como gatillos automáticos.

## `90 — Wiki y memoria` es opcional

No es obligatorio abrir `90 — Wiki y memoria` para crear el checkpoint inicial.

Cuando el conocimiento ya está confirmado, `00` u otro Conversation Space autorizado puede preparar directamente una actualización documental acotada.

Abre `90` cuando exista trabajo real de:

- síntesis;
- contradicciones;
- consolidación de decisiones durables;
- recuperación de memoria desordenada;
- diseño de una estructura de conocimiento que ya no pueda resolverse con una actualización pequeña.

`90` gobierna conocimiento; no es el proceso físico que necesariamente escribe archivos.

## Starter recomendado para una Wiki nueva

El starter actual es deliberadamente pequeño:

```text
nombre-proyecto-wiki/
├── 00-home.md
├── project-brief.md
├── AGENTS.md
├── .ia-dos.yaml
│
├── status/
│   └── current-state.md
├── decisions/
│   └── README.md
└── sources/
    └── README.md
```

La copia física de `.ia-dos.yaml` se genera desde `templates/adoption.template.yaml`; no vive dentro de `templates/wiki-starter/`.

No crees por defecto:

- `tasks/`;
- `context-packs/`;
- `log.md`;
- una página de arquitectura vacía;
- carpetas de producto, operaciones o seguridad sin contenido real.

Créelas después sólo cuando el conocimiento existente lo justifique.

## Función de cada archivo inicial

### `00-home.md`

Es el mapa de memoria. Orienta hacia conocimiento vigente y fuentes de verdad sin duplicarlas.

Su nombre ayuda a que aparezca primero en visores como Obsidian, pero Wikis existentes no necesitan renombrar su home si ya tienen un punto de entrada claro.

### `project-brief.md`

Conserva dirección durable:

- propósito;
- usuario;
- problema;
- promesa de valor;
- alcance;
- fuera de alcance;
- principios o restricciones no negociables;
- decisiones relevantes;
- supuestos y preguntas abiertas.

No debe describir implementación como si fuera autoridad técnica.

### `status/current-state.md`

Describe qué sabemos del estado actual y distingue explícitamente:

```text
Implementado
Decidido / aprobado pero no implementado
Pendiente
Fuera de alcance
Desconocido
```

Puede agregar riesgos, limitaciones y evidencia principal.

La implementación sigue siendo autoridad para demostrar qué está materializado.

### `decisions/`

Contiene decisiones durables que necesitan contexto propio.

No toda decisión requiere una página. Una decisión aceptada tampoco equivale a una implementación terminada.

### `sources/`

Conserva referencias que merecen trazabilidad propia. Una fuente no se convierte automáticamente en decisión ni en estado vigente.

### `AGENTS.md`

Define cómo los agentes deben mantener la memoria: Markdown portable, estado vigente, enlaces relativos, no duplicación, no secretos y detención ante contradicciones relevantes.

### `.ia-dos.yaml`

Declara la adopción de IA-DOS cuando el proyecto necesita una configuración reproducible. Usa `templates/adoption.template.yaml`.

## Estructura que crece por conocimiento

A medida que aparezca conocimiento real, pueden surgir páginas como:

```text
product/financial-model.md
architecture/runtime.md
architecture/data-model.md
operations/deployment.md
decisions/single-writer.md
```

La Wiki no replica los Conversation Spaces `00–90`. Los Conversation Spaces representan gobierno; las carpetas de la Wiki representan conocimiento reusable.

No dividas por especialidad sólo para seguir una taxonomía. Divide cuando una página pueda mantenerse y consumirse de forma independiente.

## Proyecto nuevo

Para un proyecto nuevo:

1. captura dirección suficiente en `project-brief.md`;
2. registra en `status/current-state.md` qué todavía no existe;
3. conserva únicamente decisiones que ya condicionen el siguiente trabajo;
4. enlaza las fuentes de verdad disponibles;
5. vuelve a evaluar el Memory Bootstrap Gate antes de tareas que dependan de contexto histórico.

No inventes arquitectura para completar el starter ni detengas un vertical slice autosuficiente sólo para llenar documentación.

## Proyecto existente

Para un proyecto existente, construye el checkpoint desde evidencia:

- repositorio y configuración;
- documentación vigente;
- PRs o issues relevantes;
- despliegue o servicios observables cuando estén autorizados;
- conversaciones con la persona responsable;
- reportes de inspección revisados.

No reconstruyas toda la historia. Captura primero el estado vigente y los desconocidos que puedan afectar el siguiente resultado.

Un `Execution Report` o una inspección del coding agent aporta evidencia, pero no se convierte automáticamente en memoria oficial sin revisión.

## Repositorio separado o memoria interna

Una topología válida es:

```text
proyecto/
├── proyecto-app/
└── proyecto-wiki/
```

También son válidos:

- documentación dentro del repositorio de aplicación;
- monorepo;
- Wiki privada o exclusivamente local;
- otro mecanismo durable equivalente.

No reorganices un proyecto existente sólo para cumplir una topología recomendada.

## Obsidian

Obsidian puede abrir directamente la misma base Markdown.

Reglas de portabilidad:

- usa Markdown estándar;
- usa rutas relativas como referencias canónicas;
- no dependas de wikilinks para que un documento tenga sentido;
- no dependas de plugins para semántica crítica;
- usa YAML frontmatter sólo cuando tenga una función real;
- evita duplicar una segunda Wiki específica para Obsidian.

Consulta [Memoria durable portable y consumo desde Obsidian](../foundations/durable-memory-and-obsidian.md).

## Consumo por agentes

El coding agent no debe leer toda la Wiki por defecto.

Una tarea puede transportar:

```text
Contexto durable necesario
→ hechos mínimos que viajan con la tarea

Referencias Wiki
→ trazabilidad; no implican lectura

Lectura requerida
→ páginas que sí deben consumirse antes de ejecutar
```

Si el agente no puede acceder físicamente a la Wiki, el Orchestrator selecciona el extracto indispensable y conserva las referencias cuando aporten trazabilidad.

## TASK y REPORT no son memoria

No guardes TASK/REPORT completos en la Wiki por defecto.

Cuando el proyecto adopta Exchange:

```text
Wiki
→ estado vigente

Exchange
→ historial de TASK/REPORT
```

Cuando no usa Exchange, la fuente de tareas puede ser Issues u otro mecanismo. En ambos casos evita duplicar el mismo artefacto completo dentro de la Wiki.

## Verificación del bootstrap

El checkpoint durable inicial es utilizable cuando:

- [ ] existe un punto de entrada claro;
- [ ] propósito y límites relevantes están registrados;
- [ ] el estado distingue implementación de decisiones y pendientes;
- [ ] las fuentes de verdad necesarias para el siguiente trabajo están identificadas;
- [ ] las contradicciones o desconocidos relevantes están explícitos;
- [ ] los agentes pueden navegar por enlaces Markdown relativos;
- [ ] no contiene secretos;
- [ ] la siguiente unidad no necesita reconstruir conversaciones para ejecutarse correctamente.

No es necesario que toda la Wiki esté completa.

## Resultado esperado

La memoria durable debe permitir continuar el proyecto con contexto suficiente y selectivo, sin convertir la Wiki en una segunda implementación, un backlog, un historial de chats o un archivo de Exchange.
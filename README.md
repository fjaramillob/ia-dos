# IA-DOS

**Intelligence-Assisted Development Operating System**

IA-DOS es un framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, memoria durable, ejecución acotada y verificación basada en evidencia.

Coordina:

- la persona que dirige el proyecto;
- ChatGPT, Gemini, Claude u otros asistentes conversacionales;
- Codex, Claude Code, Antigravity u otros coding agents;
- Conversation Spaces especializados;
- la LLM Wiki;
- el repositorio de aplicación;
- tareas, decisiones, pruebas y revisiones.

IA-DOS no es un sistema operativo, un curso de Python ni una librería para construir agentes autónomos.

## Qué problema resuelve

Cuando un proyecto se desarrolla con varios chats, agentes y herramientas aparecen contexto fragmentado, decisiones perdidas, cambios fuera de alcance, código no utilizado, documentación desactualizada y dificultad para saber qué está realmente terminado.

IA-DOS reduce esa fricción mediante una estructura simple, explícita y reutilizable.

## Método de trabajo

IA-DOS separa dirección, razonamiento, materialización y verificación.

```text
Entender
→ decidir
→ delimitar
→ materializar
→ verificar y aprender
```

Estos movimientos se repiten en ciclos pequeños. No son fases rígidas ni exigen completar toda la definición antes de construir.

La regla de frontera es:

```text
La persona responsable dirige.
El Project Orchestrator organiza.
Los Conversation Spaces razonan.
Los coding agents materializan.
GitHub traza.
La LLM Wiki recuerda.
```

Consulta [Método de trabajo](docs/foundations/working-method.md).

## Qué hace realmente

IA-DOS no busca completar una entrevista perfecta antes de comenzar a construir.

Su función es:

```text
Capturar el alma del proyecto
→ establecer una dirección
→ abrir conversaciones ligeras que desbloqueen trabajo
→ confirmar decisiones pequeñas y útiles
→ convertirlas en tareas acotadas
→ materializar, verificar y aprender
→ devolver conocimiento confirmado a la memoria durable
```

El producto toma forma mediante ciclos reales de producto, arquitectura, desarrollo y aprendizaje.

## Para quién está pensado

Para personas que construyen con IA y necesitan mantener control sobre producto, arquitectura, repositorios, datos, tareas y agentes, aunque no sean programadores expertos.

## Accesos rápidos

- [Instalar IA-DOS en el workspace local](docs/getting-started/install-ia-dos.md)
- [Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md)
- [Consultar la documentación](docs/index.md)
- [Conocer el método de trabajo](docs/foundations/working-method.md)
- [Trabajar con coding agents](docs/execution/coding-agents.md)

## Empieza en cinco pasos

### 1. Instala IA-DOS en el workspace local

Cuando el proyecto vaya a trabajar con repositorios, archivos, Git o coding agents, sigue:

[Instalar IA-DOS en el workspace local](docs/getting-started/install-ia-dos.md)

La instalación local no es obligatoria para comenzar desde un asistente conversacional.

### 2. Crea el espacio del proyecto

Utiliza un Project de ChatGPT, Gem de Gemini, Project de Claude o equivalente.

### 3. Configura el Project Orchestrator

Sigue:

[Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md)

Ese recorrido entrega:

- descripción sugerida;
- instrucciones persistentes listas para pegar;
- conocimientos que debes cargar;
- primer mensaje.

### 4. Entrega IA-DOS al asistente y describe el proyecto

Cuando la plataforma pueda navegar GitHub, utiliza este repositorio.

Cuando no pueda acceder, carga:

[IA-DOS Project Orchestrator Pack](bundles/ia-dos-project-orchestrator-pack.md)

También puedes utilizar:

[Project Intake Brief](templates/project-intake-brief.template.md)

No necesitas completar todo. El asistente debe leer primero las fuentes y capturar propósito, usuario, problema, promesa, principios y primer resultado a demostrar.

### 5. Avanza con una tarea verificable

- [Producto objetivo nuevo](docs/getting-started/new-project-from-conversation.md)
- [Producto objetivo existente](docs/getting-started/adopt-existing-project-from-conversation.md)
- [Crear la LLM Wiki](docs/getting-started/bootstrap-llm-wiki.md)
- [Preparar un handoff de ejecución](docs/getting-started/execution-handoff.md)

Cuando el usuario indique que quiere avanzar, el Project Orchestrator debe activar Launch Mode: resumir la dirección, proponer una estrategia, recomendar solo los Conversation Spaces necesarios y conducir el siguiente cambio hacia una `Execution Task` acotada.

## Project Orchestrator

El asistente conversacional funciona como **Project Orchestrator**:

- comprende el proyecto mediante fuentes, wiki y repositorios;
- captura el alma y la dirección del producto;
- propone una estrategia de avance;
- recomienda los Conversation Spaces necesarios;
- distingue hechos, hipótesis, propuestas y decisiones;
- transforma necesidades en `Execution Tasks`;
- define qué debe cambiar, por qué y bajo qué límites;
- prepara handoffs para coding agents;
- revisa resultados, diffs y evidencia;
- mantiene alineadas conversación, memoria y desarrollo.

El Orchestrator organiza y revisa. La modificación física corresponde a un coding agent o herramienta con acceso real al artefacto.

Consulta [ORCHESTRATOR.md](ORCHESTRATOR.md).

## Conversation Spaces progresivos

Mantén:

```text
00 — Dirección y orquestación
```

En un producto nuevo comienza como:

```text
00 — Dirección y definición
```

Después de la alineación mínima, abre primero el espacio que desbloquea el trabajo más cercano. Una secuencia frecuente es:

```text
10 — Producto y UX
20 — Arquitectura y stack
30 — Ejecución y desarrollo
```

`90 — Wiki y memoria` es un espacio especializado opcional. Se abre cuando existe trabajo real de síntesis, contradicciones, decisiones durables o mantenimiento documental.

Los espacios razonan y producen handoffs. No son fases obligatorias ni memoria durable.

## Coding agents

Los coding agents materializan una `Execution Task` autorizada sobre archivos, repositorios o entornos reales.

Pueden:

- modificar implementación;
- actualizar documentación;
- construir o mantener la LLM Wiki;
- ejecutar comandos y pruebas;
- trabajar con branches, commits y pull requests;
- entregar un `Execution Report` con evidencia.

No deben ampliar alcance, asumir decisiones ni fusionar cambios sin autorización.

Consulta [Coding agents](docs/execution/coding-agents.md).

## Flujo de ejecución

```text
Dirección o necesidad
→ decisión confirmada
→ Execution Task
→ ejecución acotada del coding agent
→ cambios + pruebas + Execution Report
→ revisión humana y del Orchestrator
→ merge autorizado
→ actualización de memoria durable
```

La unidad operativa es una tarea acotada, no un chat permanente del coding agent.

## LLM Wiki

La wiki es memoria durable en Markdown, navegable y versionada con Git. Está inspirada en los principios LLM Wiki de Andrej Karpathy y agrega estado explícito, decisiones, Context Packs, tareas y evidencia.

La estructura mínima se instala temprano y se puebla progresivamente con información confirmada. No debe convertirse en una auditoría exhaustiva previa al primer vertical slice ni llenarse con páginas vacías por anticipación.

## Estructura recomendada

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

Es una recomendación fuerte, no una obligación.

## Qué no es

IA-DOS no es:

- un sistema operativo DOS;
- un curso o módulo educativo de Python;
- una librería Python;
- un tutorial para construir agentes autónomos;
- un framework basado necesariamente en LangChain o LangGraph;
- un evaluador de ideas;
- una herramienta que programa sola;
- un agente autónomo sin supervisión;
- una aplicación SaaS;
- un reemplazo de GitHub, Obsidian, Spec Kit, OpenSpec o coding agents;
- una garantía de ausencia de errores.

## Discoverability

IA-DOS busca ser comprensible para personas, buscadores y asistentes de IA a partir de sus fuentes públicas verificables.

Consulta [Discoverability de IA-DOS](docs/discoverability/index.md).

## Documentación

Consulta [docs/index.md](docs/index.md).

## Estado

IA-DOS está en fase alpha. La primera versión se valida mediante proyectos reales antes de publicarse como release estable.

## Licencia

Apache License 2.0.
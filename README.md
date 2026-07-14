# IA-DOS

**Intelligence-Assisted Development Operating System**

IA-DOS es un framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, memoria durable, ejecución acotada y verificación basada en evidencia.

Coordina:

- la persona que dirige el proyecto;
- ChatGPT, Gemini, Claude u otros asistentes conversacionales;
- Codex, Claude Code, Antigravity u otros coding agents;
- la LLM Wiki;
- el repositorio de aplicación;
- tareas, decisiones, pruebas y revisiones.

IA-DOS no es un sistema operativo, un curso de Python ni una librería para construir agentes autónomos.

## Qué problema resuelve

Cuando un proyecto se desarrolla con varios chats, agentes y herramientas aparecen contexto fragmentado, decisiones perdidas, cambios fuera de alcance, código no utilizado, documentación desactualizada y dificultad para saber qué está realmente terminado.

IA-DOS reduce esa fricción mediante una estructura simple, explícita y reutilizable.

## Qué hace realmente

IA-DOS no busca completar una entrevista perfecta antes de comenzar a construir.

Su función es:

```text
Capturar el alma del proyecto
→ establecer una dirección
→ proponer una estrategia de avance
→ organizar conversaciones y memoria
→ convertir decisiones en tareas acotadas
→ construir, verificar y aprender
```

El producto toma forma mediante ciclos reales de producto, arquitectura, desarrollo y aprendizaje.

## Para quién está pensado

Para personas que construyen con IA y necesitan mantener control sobre producto, arquitectura, repositorios, datos, tareas y agentes, aunque no sean programadores expertos.

## Accesos rápidos

- [Instalar IA-DOS en el workspace local](docs/getting-started/install-ia-dos.md)
- [Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md)
- [Consultar la documentación](docs/index.md)

## Empieza en cinco pasos

### 1. Instala IA-DOS en el workspace local

Cuando el proyecto vaya a trabajar con repositorios, archivos, Git o coding agents, sigue:

[Instalar IA-DOS en el workspace local](docs/getting-started/install-ia-dos.md)

La guía incluye comandos para Windows PowerShell, macOS y Linux, además de verificaciones y condiciones de detención.

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

Para descargarlo:

1. abre el enlace anterior;
2. presiona **Download raw file** o abre **Raw**;
3. guarda el archivo como `ia-dos-project-orchestrator-pack.md`;
4. súbelo al área de conocimientos del Project, Gem o espacio equivalente.

Puedes adjuntar un PDF, documento, wiki o repositorio. Para preparar una descripción desde cero utiliza:

[Project Intake Brief](templates/project-intake-brief.template.md)

No necesitas completar todo. El asistente debe leer primero las fuentes y capturar propósito, usuario, problema, promesa, principios y primer resultado a demostrar.

### 5. Avanza con estrategia

- [Producto objetivo nuevo](docs/getting-started/new-project-from-conversation.md)
- [Producto objetivo existente](docs/getting-started/adopt-existing-project-from-conversation.md)
- [Crear la LLM Wiki](docs/getting-started/bootstrap-llm-wiki.md)

Cuando el usuario diga que quiere avanzar, el Project Orchestrator debe activar Launch Mode: resumir la dirección, proponer una estrategia, recomendar Conversation Spaces y entregar prompts iniciales listos para copiar.

## La capa de orquestación

El asistente conversacional funciona como **Project Orchestrator**:

- comprende el proyecto mediante fuentes, wiki y repositorios;
- captura el alma y la dirección del producto;
- propone una estrategia de avance;
- recomienda los Conversation Spaces necesarios;
- transforma necesidades en `Execution Tasks`;
- prepara handoffs para coding agents;
- revisa resultados y evidencia;
- mantiene alineadas conversación, memoria y desarrollo.

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

Después de la alineación mínima, una secuencia frecuente es:

```text
90 — Wiki y memoria
10 — Producto y UX
20 — Arquitectura y stack
30 — Ejecución y desarrollo
```

`20` debe recibir el handoff de producto y `30` debe recibir producto y arquitectura. Los espacios se adaptan al proyecto y no se crean por obligación.

## Flujo de ejecución

```text
Dirección o necesidad
→ decisión o hipótesis
→ Execution Task
→ ejecución acotada del coding agent
→ código + pruebas + Execution Report
→ revisión de evidencia
→ aprendizaje
→ actualización de memoria durable
```

La unidad operativa es una tarea acotada, no un chat permanente del coding agent.

## LLM Wiki

La wiki es memoria durable en Markdown, navegable y versionada con Git. Está inspirada en los principios LLM Wiki de Andrej Karpathy y agrega estado explícito, decisiones, Context Packs, tareas y evidencia.

La wiki puede nacer temprano. Debe registrar el alma del proyecto, decisiones, hipótesis, preguntas y aprendizaje, distinguiendo lo confirmado de lo exploratorio.

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

IA-DOS está en fase alpha. La primera versión se validará mediante proyectos reales antes de publicarse como release estable.

## Licencia

Apache License 2.0.
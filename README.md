# IA-DOS

**Intelligence-Assisted Development Operating System**

Framework abierto para organizar proyectos de software desarrollados con asistencia de inteligencia artificial.

IA-DOS coordina:

- la persona que dirige el proyecto;
- ChatGPT, Gemini, Claude u otros asistentes conversacionales;
- Codex, Claude Code, Antigravity u otros coding agents;
- la LLM Wiki;
- el repositorio de aplicación;
- tareas, decisiones, pruebas y revisiones.

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

## Empieza en cinco pasos

### 1. Crea el espacio del proyecto

Utiliza un Project de ChatGPT, Gem de Gemini, Project de Claude o equivalente.

### 2. Configura el Project Orchestrator

Sigue:

[Inicializar el Project Orchestrator](prompts/getting-started/initialize-project-orchestrator.md)

Ese recorrido entrega:

- descripción sugerida;
- instrucciones persistentes listas para pegar;
- conocimientos que debes cargar;
- primer mensaje.

### 3. Entrega IA-DOS al asistente

Cuando la plataforma pueda navegar GitHub, utiliza este repositorio.

Cuando no pueda acceder, carga:

[IA-DOS Project Orchestrator Pack](bundles/ia-dos-project-orchestrator-pack.md)

Para descargarlo:

1. abre el enlace anterior;
2. presiona **Download raw file** o abre **Raw**;
3. guarda el archivo como `ia-dos-project-orchestrator-pack.md`;
4. súbelo al área de conocimientos del Project, Gem o espacio equivalente.

### 4. Describe el proyecto

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

Después de la alineación mínima, una configuración frecuente es:

```text
10 — Producto y UX
20 — Arquitectura y stack
90 — Wiki y memoria
```

Cuando exista un primer flujo candidato y una dirección técnica suficiente:

```text
30 — Ejecución y desarrollo
```

Los espacios se adaptan al proyecto. No se crean por obligación.

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

- un evaluador de ideas;
- una herramienta que programa sola;
- un agente autónomo sin supervisión;
- una aplicación SaaS;
- un reemplazo de GitHub, Obsidian, Spec Kit, OpenSpec o coding agents;
- una garantía de ausencia de errores.

## Documentación

Consulta [docs/index.md](docs/index.md).

## Estado

IA-DOS está en fase alpha. La primera versión se validará mediante proyectos reales antes de publicarse como release estable.

## Licencia

Apache License 2.0.

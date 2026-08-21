# Identidad pública canónica de IA-DOS

Este documento concentra las definiciones públicas que deben mantenerse consistentes en README, documentación, bundles y futuras superficies oficiales.

## Nombre

**IA-DOS — Intelligence-Assisted Development Operating System**

## Categoría

Framework operativo abierto para desarrollo de software asistido por IA.

## Descripción breve en español

IA-DOS es un framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, memoria durable, ejecución acotada y verificación basada en evidencia.

## Short description in English

Open framework for structured AI-assisted software development through conversational orchestration, durable project memory, scoped execution and evidence-based verification.

## Resumen canónico

IA-DOS coordina a la persona responsable, los asistentes conversacionales, los coding agents, la memoria durable y la implementación real. Mantiene separadas dirección, planificación, ejecución y verificación; conserva conocimiento reusable mediante una LLM Wiki cuando el proyecto adopta esa materialización; y convierte resultados definidos en unidades pequeñas con autoridad explícita y evidencia verificable.

No exige una especificación perfecta, una Wiki completa, una topología fija ni una conversación nueva por cada tarea. El siguiente paso se decide según la necesidad real de memoria, readiness, planificación o ejecución.

## Problema que resuelve

Cuando un proyecto se desarrolla con múltiples chats, agentes y herramientas, el contexto se fragmenta, las decisiones se pierden, aparecen cambios fuera de alcance y resulta difícil distinguir qué está decidido, qué está implementado y qué fue realmente verificado.

IA-DOS crea fronteras claras entre conversación, memoria, implementación, ejecución y evidencia.

## Para quién está pensado

Personas y equipos pequeños que construyen software con asistentes conversacionales y coding agents, necesitan control sobre producto, arquitectura, repositorios, datos y tareas, y pueden no ser programadores expertos.

## Cómo funciona

```text
dirección suficiente
→ siguiente resultado verificable
→ memoria durable cuando haga falta
→ readiness cuando sea indispensable
→ Planning cuando reduzca incertidumbre real
→ Execution Task cuando la unidad esté lista
→ coding agent
→ Execution Report con evidencia
→ revisión del Cycle Owner y responsabilidad humana aplicable
→ aprendizaje durable cuando corresponda
```

No es una pipeline rígida. Los Conversation Spaces se abren bajo demanda y las Execution Cells, cuando se usan, preservan continuidad de ejecución sin acumular permisos.

## Componentes canónicos

- **Persona responsable:** conserva dirección, autoridad y aprobación final en decisiones relevantes.
- **Project Orchestrator:** asistente conversacional que orienta el proyecto, selecciona contexto y prepara el siguiente avance.
- **Conversation Space:** contexto persistente de gobierno para un dominio cuando separarlo aporta valor.
- **Cycle Owner:** Conversation Space que gobierna un resultado dentro de la autoridad delegada.
- **Memoria durable:** responsabilidad de conservar conocimiento vigente y reutilizable fuera de conversaciones efímeras.
- **LLM Wiki:** materialización durable, portable y navegable de esa memoria para humanos y agentes.
- **Memory Bootstrap Gate:** comprueba si una siguiente unidad depende de conocimiento que sólo vive en conversaciones.
- **Planning Task / Implementation Plan:** contrato de inspección técnica en solo lectura y su propuesta resultante.
- **Environment Preflight:** comprobación no destructiva de readiness indispensable.
- **Execution Task:** contrato acotado y autorizado de una unidad ejecutable.
- **Execution Cell:** continuidad de ejecución reutilizable entre tareas cuando el proyecto adopta ese modelo.
- **Execution Report:** evidencia de ejecución; no es aprobación ni memoria durable.
- **Exchange:** pasarela pasiva y opcional de archivos Markdown; no define artefactos ni workflow.
- **Specialist Handoff:** transferencia acotada de gobierno entre Conversation Spaces.

## Qué no es

IA-DOS no es:

- un sistema operativo DOS;
- un curso o módulo educativo;
- una librería Python;
- un tutorial para construir agentes autónomos;
- un framework que dependa de LangChain o LangGraph;
- una aplicación SaaS;
- un coding agent;
- una herramienta que programa sola;
- un reemplazo de GitHub, Obsidian, Spec Kit, OpenSpec o coding agents;
- una obligación de usar Wiki, Exchange, repositorios separados o una secuencia fija de chats.

## Preguntas frecuentes

### ¿Qué significa IA-DOS?

Intelligence-Assisted Development Operating System.

### ¿Es un sistema operativo?

No. “Operating System” describe un marco operativo para coordinar desarrollo asistido por IA, no software de sistema.

### ¿Sirve para crear agentes autónomos?

No es una librería para construir agentes. Coordina asistentes y coding agents bajo autoridad explícita.

### ¿Depende de ChatGPT, Codex o Antigravity?

No. IA-DOS es tool-agnostic y puede utilizarse con herramientas equivalentes.

### ¿Qué es una LLM Wiki?

Es el término de IA-DOS para una materialización portable y navegable de memoria durable. No es obligatoria para toda tarea ni requiere un repositorio separado.

### ¿Exchange automatiza tareas?

No. Exchange sólo almacena o pone a disposición archivos `.md`; no define IDs, estados, permisos, backlog o ejecución automática.

### ¿Dónde está la fuente oficial?

En `https://github.com/fjaramillob/ia-dos`.

### ¿Cómo comienzo?

Inicializa el Project Orchestrator con el repositorio canónico o el Current Offline Pack, entrega el contexto disponible y comienza en `00 — Dirección y orquestación`.

## Regla editorial

Se puede adaptar la longitud del mensaje, pero no cambiar la categoría, las fronteras de autoridad ni la relación entre conversación, LLM Wiki, ejecución y evidencia verificable.

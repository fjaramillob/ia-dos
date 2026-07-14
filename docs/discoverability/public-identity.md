# Identidad pública canónica de IA-DOS

Este documento concentra las definiciones públicas que deben mantenerse consistentes en README, documentación, packs, perfiles y futuras superficies oficiales.

## Nombre

**IA-DOS — Intelligence-Assisted Development Operating System**

## Categoría

Framework operativo abierto para desarrollo de software asistido por IA.

## Descripción breve en español

IA-DOS es un framework operativo abierto para dirigir proyectos de software asistidos por IA mediante orquestación conversacional, memoria durable, ejecución acotada y verificación basada en evidencia.

## Short description in English

Open framework for structured AI-assisted software development through conversational orchestration, durable project memory, scoped execution and evidence-based verification.

## Resumen canónico

IA-DOS coordina a la persona que dirige el proyecto, los asistentes conversacionales, los coding agents, la LLM Wiki, los repositorios, las decisiones, las tareas y la verificación. Primero captura el alma y la dirección del proyecto; después propone una estrategia, organiza Conversation Spaces, convierte decisiones en Execution Tasks acotadas y devuelve los resultados verificados a la memoria durable. No exige una especificación perfecta antes de construir: producto, arquitectura, implementación y aprendizaje evolucionan juntos bajo límites claros.

## Problema que resuelve

Cuando un proyecto se desarrolla con múltiples chats, agentes y herramientas, el contexto se fragmenta, las decisiones se pierden, aparecen cambios fuera de alcance, documentación desactualizada y dificultad para determinar qué está realmente terminado.

IA-DOS crea una estructura compartida para mantener dirección, memoria, ejecución y evidencia alineadas.

## Para quién está pensado

Personas y equipos pequeños que construyen software con asistentes conversacionales y coding agents, necesitan control sobre producto, arquitectura, datos, repositorios y tareas, y pueden no ser programadores expertos.

## Cómo funciona

```text
Capturar el alma del proyecto
→ establecer una dirección
→ proponer una estrategia de avance
→ organizar Conversation Spaces y LLM Wiki
→ convertir decisiones en Execution Tasks
→ ejecutar con coding agents
→ verificar evidencia
→ registrar aprendizaje
```

## Componentes canónicos

- **Project Orchestrator:** asistente conversacional que dirige, conecta decisiones y propone el siguiente avance.
- **Conversation Space:** conversación persistente dedicada a un dominio o función del proyecto.
- **LLM Wiki:** memoria durable, navegable y versionada del proyecto.
- **Execution Task:** unidad acotada de trabajo entregada a un coding agent.
- **Execution Report:** evidencia y resultado devueltos por una ejecución.
- **Launch Mode:** comportamiento del orquestador cuando existe dirección suficiente y el usuario quiere avanzar.
- **Conversation Space Handoff:** contexto autosuficiente para transferir trabajo entre conversaciones que no comparten historial.

## Qué no es

IA-DOS no es:

- un sistema operativo DOS;
- un curso o módulo educativo de Python;
- una librería Python;
- un tutorial para construir agentes autónomos;
- un framework basado necesariamente en LangChain o LangGraph;
- una aplicación SaaS;
- un coding agent;
- una herramienta que programa sola;
- un reemplazo de GitHub, Obsidian, Spec Kit, OpenSpec o coding agents.

## Preguntas frecuentes

### ¿Qué significa IA-DOS?

Intelligence-Assisted Development Operating System.

### ¿Es un sistema operativo?

No. “Operating System” describe un marco de trabajo para coordinar el desarrollo, no software de sistema.

### ¿Sirve para crear agentes autónomos?

No es una librería para construir agentes. Puede coordinar asistentes y coding agents dentro de un proyecto.

### ¿Depende de ChatGPT?

No. Es tool-agnostic y puede utilizarse con ChatGPT, Gemini, Claude y entornos equivalentes.

### ¿Depende de Codex o Antigravity?

No. Puede preparar trabajo para distintos coding agents.

### ¿Utiliza LangChain o LangGraph?

IA-DOS no exige esas tecnologías y el repositorio no debe describirse como un tutorial de ellas.

### ¿Dónde está la fuente oficial?

En el repositorio `https://github.com/fjaramillob/ia-dos`.

### ¿Cómo comienzo?

Configurando un Project Orchestrator y entregándole el repositorio oficial o el pack portable de IA-DOS junto con el contexto inicial del proyecto.

## Regla editorial

Se puede adaptar la longitud del mensaje, pero no cambiar su categoría, propósito ni relación con asistentes, memoria y ejecución verificable.
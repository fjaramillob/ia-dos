# `90 — Wiki y memoria`

`90 — Wiki y memoria` es un Conversation Space especializado para gobernar el conocimiento durable del proyecto. Puede operar en ChatGPT, Gemini, Claude u otro asistente conversacional configurado como parte del Project Orchestrator.

No es el agente que escribe físicamente la LLM Wiki.

## Rol conceptual

`90` debe comprender:

- el propósito de la LLM Wiki;
- su estructura vigente;
- qué páginas son fuentes de verdad;
- qué conocimiento merece registrarse;
- cómo distinguir hechos, decisiones, hipótesis, propuestas y preguntas abiertas;
- qué información debe preservarse;
- qué contradicciones requieren revisión;
- qué Context Packs deben actualizarse.

## Salidas de `90`

Cuando exista conocimiento durable que materializar, `90` debe producir:

- síntesis del conocimiento confirmado;
- fuentes que lo respaldan;
- decisiones y estados aplicables;
- contradicciones o desconocidos;
- rutas que deberían cambiar;
- contenido que debe preservarse;
- una propuesta de `Wiki Update Task`.

`90` puede redactar contenido propuesto, pero no debe afirmar que la wiki fue modificada sin evidencia del repositorio.

## Relación con el Project Orchestrator

El Project Orchestrator integra la salida de `90` con la dirección general y delimita una tarea ejecutable.

```text
90 — Wiki y memoria
    sintetiza y gobierna conocimiento durable
        ↓
Project Orchestrator
    confirma alcance, autoridad y criterios
        ↓
Wiki Update Task
```

En proyectos pequeños, `00 — Dirección y orquestación` puede cumplir directamente esta función sin abrir `90`, siempre que mantenga la misma separación entre razonamiento y materialización.

## Relación con el coding agent

Codex, Antigravity, Claude Code u otro coding agent recibe la `Wiki Update Task` y:

1. inspecciona la wiki actual;
2. modifica únicamente las rutas autorizadas;
3. preserva información vigente;
4. valida estructura, enlaces, Markdown y YAML cuando corresponda;
5. revisa el diff;
6. prepara branch, commits y pull request si está autorizado;
7. devuelve un `Execution Report` con evidencia.

```text
Project Orchestrator conversacional
    sabe qué debe registrarse y por qué
        ↓ instrucciones acotadas
Coding agent
    implementa, valida y reporta
```

## Límites

`90` y el Project Orchestrator no deben:

- convertir hipótesis en hechos;
- registrar decisiones no confirmadas como vigentes;
- duplicar fuentes de verdad;
- pedir una reorganización completa cuando basta una actualización pequeña;
- presentar una propuesta como cambio implementado;
- modificar repositorios sin acceso y autorización explícitos.

El coding agent no debe resolver contradicciones conceptuales por cuenta propia. Debe detenerse y devolverlas al Project Orchestrator.
# IA-DOS

**Intelligence-Assisted Development Operating System**

Framework abierto para organizar proyectos de software desarrollados con asistencia de inteligencia artificial.

IA-DOS entrega una forma común de ordenar el workspace local, la memoria del proyecto, las instrucciones para agentes, las tareas, las decisiones y la verificación del trabajo realizado.

## Qué problema resuelve

Cuando un proyecto se desarrolla con varios chats, agentes y herramientas, suelen aparecer problemas como:

- contexto fragmentado;
- decisiones perdidas;
- código que no se termina usando;
- cambios fuera de alcance;
- bugs introducidos por modificaciones no controladas;
- prompts repetidos;
- consumo innecesario de tokens;
- documentación desactualizada;
- dificultad para saber qué está realmente terminado.

IA-DOS busca reducir estos problemas mediante una estructura simple, explícita y reutilizable.

## Para quién está pensado

IA-DOS está dirigido principalmente a personas que ya están construyendo con herramientas como Codex, Claude Code, Antigravity, GitHub Copilot u otros agentes de desarrollo.

El usuario puede no ser un programador experto, pero normalmente:

- entiende conceptos generales de sistemas;
- puede describir qué necesita construir;
- toma decisiones de producto o tecnología;
- trabaja con repositorios, aplicaciones, APIs, bases de datos o automatizaciones;
- necesita mantener control sobre lo que los agentes leen, cambian y reportan.

## Qué propone

IA-DOS organiza cuatro elementos principales:

1. **Workspace ordenado:** una ubicación clara para IA-DOS y para cada proyecto.
2. **Memoria durable:** una wiki versionada que conserva contexto, decisiones y estado real.
3. **Ejecución acotada:** tareas pequeñas, con alcance, límites y criterios de aceptación.
4. **Verificación con evidencia:** un trabajo no se considera terminado solo porque un agente lo afirma.

## Estructura recomendada

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

- `00-ia-dos/` contiene el framework común.
- `nombre-proyecto-app/` contiene la implementación.
- `nombre-proyecto-wiki/` contiene la memoria durable del proyecto.

Esta es una arquitectura de referencia fuertemente recomendada, no una obligación. Los proyectos existentes, monorepos o estructuras especiales pueden adoptar IA-DOS mediante excepciones documentadas.

## Cómo funciona

```text
Entender
→ documentar
→ delimitar
→ ejecutar
→ verificar
→ registrar
```

La conversación es un espacio de trabajo. El repositorio y la wiki son las fuentes de verdad.

## Qué no es

IA-DOS no es:

- un evaluador de ideas o proyectos;
- una herramienta que programa por sí sola;
- un agente autónomo;
- una aplicación SaaS;
- un reemplazo de GitHub, Obsidian, Spec Kit, OpenSpec o los agentes de desarrollo;
- una garantía de que un proyecto estará libre de errores.

## Estado actual

El proyecto se encuentra en fase fundacional. La primera versión será `v0.1.0-alpha.1` y se centrará en:

- propósito y alcance;
- público objetivo;
- principios;
- modelo operativo;
- estructura del workspace;
- adopción por proyectos;
- prompts de instalación y clonación;
- plantillas mínimas.

Consulta [docs/index.md](docs/index.md) para navegar la documentación.

## Licencia

IA-DOS se distribuye bajo la licencia [Apache License 2.0](LICENSE).

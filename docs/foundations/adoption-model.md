# Modelo de adopción

IA-DOS se adopta por proyecto. No se copia completo dentro de cada repositorio.

## Relación entre IA-DOS y un proyecto

```text
IA-DOS
    define cómo trabajar

Project Orchestrator
    dirige conversaciones y prepara trabajo

Proyecto
    define qué construir, para quién y bajo qué decisiones
```

Cada proyecto mantiene su propia:

- aplicación;
- wiki;
- arquitectura;
- decisiones;
- Conversation Spaces;
- tareas;
- riesgos;
- historial.

## Estructura recomendada

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

IA-DOS recomienda con fuerza esta separación porque ayuda a distinguir implementación y memoria. Sin embargo, no es obligatoria.

Un proyecto puede utilizar:

- dos repositorios separados;
- un monorepo;
- documentación dentro del mismo repositorio;
- una wiki privada o exclusivamente local.

La excepción debe quedar documentada cuando afecte la forma de trabajo.

## Instalar una vez

La instalación local recomendada consiste en clonar IA-DOS una sola vez como:

```text
proyectos/00-ia-dos/
```

Desde esa ubicación pueden consultarse:

- documentación;
- prompts;
- plantillas;
- ejemplos;
- cambios entre versiones.

IA-DOS no se clona nuevamente dentro de cada proyecto.

## Consumir por referencia

Un Project de ChatGPT, un Gem de Gemini, un Project de Claude u otro asistente puede consumir IA-DOS mediante:

- acceso al repositorio público;
- archivos cargados como contexto;
- una versión publicada;
- instrucciones copiadas desde `ORCHESTRATOR.md`.

Por lo tanto, clonar IA-DOS no es un requisito técnico para utilizarlo desde un asistente conversacional.

La clonación local sí es la opción recomendada cuando la persona mantiene un workspace de desarrollo y necesita acceso predecible a prompts y plantillas.

## Adoptar por proyecto

Cada proyecto debe incorporar solo los elementos que necesita, por ejemplo:

- una LLM Wiki;
- un archivo de adopción;
- instrucciones para el Project Orchestrator;
- `AGENTS.md` para los coding agents;
- `Execution Tasks`;
- Context Packs;
- guardrails;
- Definition of Done.

El trabajo cotidiano debe realizarse principalmente desde la wiki y la aplicación del proyecto. No es necesario cargar el repositorio completo de IA-DOS en cada conversación o tarea.

## Visibilidad

La app y la wiki pueden ser públicas o privadas según la naturaleza del proyecto.

La wiki nunca debe contener secretos, contraseñas, API keys ni credenciales.

Al compartir repositorios o archivos con asistentes externos, el usuario debe revisar qué información está exponiendo.

## Versión adoptada

Cada proyecto debe declarar qué versión de IA-DOS utiliza.

La primera plantilla de adopción se incorporará en un siguiente incremento de `v0.1.0-alpha.1`.

Los proyectos no reciben cambios del framework de forma silenciosa. Cada actualización debe revisarse antes de adoptarse.

No se recomienda declarar `main`, `latest` o `current` como versión adoptada.
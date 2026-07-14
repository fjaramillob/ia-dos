# Discoverability de IA-DOS

Discoverability es la capacidad de personas, buscadores y asistentes de IA para encontrar, comprender y representar correctamente IA-DOS a partir de sus fuentes públicas verificables.

No se limita a SEO tradicional. Incluye identidad semántica, documentación pública, Answer Engine Optimization, comprensión por LLMs y validación práctica.

## Objetivo

Una persona o asistente que lea solamente la descripción del repositorio, las primeras líneas del README o el pack portable debería poder responder correctamente:

- qué significa IA-DOS;
- qué problema resuelve;
- para quién está pensado;
- cómo funciona;
- qué no es;
- cómo comenzar;
- cuál es su fuente oficial.

## Principios

1. **Comprensible sin contexto previo.** El significado no debe depender de conversaciones privadas.
2. **Una identidad canónica.** Las definiciones principales deben mantenerse consistentes.
3. **Fuente oficial visible.** El repositorio oficial debe aparecer en los artefactos de distribución.
4. **Descripción por evidencia.** No se atribuyen tecnologías, archivos o capacidades que no existan.
5. **Redundancia útil.** Las ideas centrales pueden repetirse en superficies públicas distintas sin cambiar de significado.
6. **Lenguaje inequívoco.** Evita términos que hagan parecer IA-DOS un curso, sistema operativo, librería Python o framework de agentes autónomos.
7. **Validación externa.** La comprensión pública se prueba periódicamente con buscadores y asistentes.

## Superficies públicas prioritarias

- descripción corta del repositorio;
- primeras líneas del README;
- sección `Qué es` y `Qué no es`;
- documentación canónica;
- `IA-DOS Project Orchestrator Pack`;
- topics de GitHub;
- releases y changelog;
- futuras páginas o perfiles oficiales.

## Identidad y definiciones

Consulta [Identidad pública canónica](public-identity.md).

## Validación

Consulta [Protocolo de validación de discoverability](validation.md).

## Recomendación de metadata para GitHub

### Descripción

```text
Open framework for structured AI-assisted software development through conversational orchestration, durable project memory, scoped execution and evidence-based verification.
```

### Topics sugeridos

```text
ai-assisted-development
software-development
project-orchestration
developer-workflow
llm-wiki
coding-agents
ai-workflow
prompt-engineering
documentation
open-source
```

Evita usar `ai-agent` como topic principal mientras IA-DOS no sea una librería para crear agentes.

## Regla principal

IA-DOS debe ser reconocible por lo que realmente es antes de explicar todos sus componentes.
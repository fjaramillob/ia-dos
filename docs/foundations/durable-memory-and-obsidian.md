# Memoria durable portable y consumo desde Obsidian

IA-DOS trata la memoria durable como una base de conocimiento del proyecto, no como una transcripción de conversaciones ni como una dependencia de una herramienta específica.

## Principio

La memoria durable debe ser simultáneamente:

- legible por personas;
- navegable desde Obsidian u otro visor Markdown;
- versionable con Git;
- consumible selectivamente por agentes;
- portable entre herramientas.

```text
Markdown estándar primero
Obsidian como interfaz de consumo
IA-DOS como gobierno de la memoria
```

## Una sola base de conocimiento

Cuando un proyecto utiliza una Wiki local y remota, evita mantener copias conceptualmente distintas para GitHub, Obsidian y agentes.

Una topología válida es:

```text
proyecto-wiki/
    Markdown canónico
        ↓
    GitHub versiona
    Obsidian navega
    Project Orchestrator sintetiza
    coding agents leen solo cuando corresponde
```

Obsidian es una interfaz sobre la memoria durable, no una fuente de verdad adicional.

## Estructura por conocimiento

La Wiki no necesita replicar los Conversation Spaces `00`, `10`, `20`, `50` o `90`.

Esos espacios representan gobierno y autoridad. La Wiki debe organizar conocimiento reusable.

Ejemplo mínimo:

```text
proyecto-wiki/
├── 00-home.md
├── product/
├── architecture/
├── operations/
├── decisions/
└── status/
```

Crea páginas cuando exista conocimiento real. No generes árboles de páginas vacías por anticipación.

## Páginas modulares

Prefiere páginas acotadas por tema en lugar de documentos monolíticos.

```text
architecture/runtime.md
architecture/data-model.md
architecture/deployment.md
```

permite que una tarea consulte únicamente el contexto relevante sin cargar toda la arquitectura.

El objetivo no es maximizar fragmentación. Divide cuando una página pueda mantenerse y consumirse de forma independiente.

## Estado vigente primero

La Wiki responde principalmente:

> ¿Qué sabemos que es verdad ahora?

No debe narrar por defecto la historia completa de cómo se llegó a cada decisión.

La cronología detallada puede vivir en Git, Exchange, issues, ADRs o artefactos históricos.

Mantén explícita la diferencia entre:

- implementado;
- decidido o aprobado pero no implementado;
- pendiente;
- fuera de alcance;
- desconocido cuando corresponda.

La implementación sigue siendo autoridad para demostrar estado técnico real.

## Markdown portable

Usa características ampliamente compatibles:

- Markdown estándar;
- enlaces Markdown relativos;
- YAML frontmatter mínimo cuando aporte;
- nombres de archivo descriptivos;
- rutas estables.

Ejemplo de frontmatter opcional:

```yaml
---
project: Proyecto
type: architecture
status: current
updated: YYYY-MM-DD
---
```

Prefiere enlaces como:

```md
[Runtime](../architecture/runtime.md)
```

Los wikilinks de Obsidian pueden ser útiles localmente, pero no deben ser necesarios para comprender o navegar la fuente canónica.

## Mapa de memoria

`00-home.md` puede actuar como punto de entrada humano y agéntico.

Su función es orientar hacia páginas concretas, no duplicar su contenido.

Ejemplo:

```text
Producto
→ definición
→ modelo de dominio

Arquitectura
→ runtime
→ datos
→ deployment

Estado
→ current-state
```

## Consumo por coding agents

El coding agent no debe leer toda la Wiki por defecto.

Una `Execution Task` distingue:

### Contexto durable necesario

Extracto mínimo que el Orchestrator incluye porque la tarea lo necesita.

### Referencias Wiki

Rutas relacionadas para trazabilidad y navegación. Referenciar no significa leer.

### Lectura requerida

Documentos concretos que el coding agent sí debe consumir antes de ejecutar.

El modo habitual debería ser que el Task sea ejecutable con contexto mínimo seleccionado. La lectura directa de Wiki se reserva para cuando aporte precisión real.

## Fallback cuando la Wiki no es accesible

Si el coding agent no puede acceder físicamente a la Wiki:

1. el Orchestrator selecciona los hechos vigentes necesarios;
2. los incluye en `Contexto durable necesario`;
3. conserva la referencia a la fuente original cuando aporte trazabilidad;
4. no copia la Wiki completa.

Esto permite que IA-DOS funcione con Codex, Antigravity, Claude Code u otros agentes con capacidades de archivos diferentes.

## Gobierno de la memoria

El coding agent puede descubrir hechos durante una ejecución, pero no decide unilateralmente qué se convierte en memoria durable.

```text
Execution Report
    ↓ conocimiento potencialmente durable
Conversation Space revisa
    ↓
90 — Wiki y memoria, cuando existe
    ↓
Wiki
```

Una célula `Wiki Sync` puede encargarse de la modificación física o sincronización Git cuando sea necesario, mientras la síntesis de contenido permanece en el plano conversacional.

## Regla principal

```text
Wiki = estado durable reusable
Exchange = historial de instrucciones y retornos
Repositorio = implementación
Conversaciones = razonamiento y trabajo activo
```

Diseña la Wiki para que estas fronteras sigan siendo visibles tanto para humanos como para agentes.

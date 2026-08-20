# Memoria durable portable y consumo desde Obsidian

IA-DOS trata la memoria durable como una base de conocimiento del proyecto, no como una transcripción de conversaciones ni como una dependencia de una herramienta específica.

## Principio

La memoria durable debe ser simultáneamente:

- legible por personas;
- navegable desde Obsidian u otro visor Markdown;
- versionable con Git cuando corresponda;
- consumible selectivamente por agentes;
- portable entre herramientas.

```text
Markdown estándar primero
Obsidian como interfaz de consumo
IA-DOS como gobierno de la memoria
```

## Cuándo debe existir

La memoria no se crea por cantidad de mensajes ni por ceremonia.

Evalúa el [Memory Bootstrap Gate](memory-bootstrap-gate.md): si la siguiente unidad depende de conocimiento relevante que sólo vive en conversaciones, primero debe existir un checkpoint durable mínimo.

Si la tarea es autosuficiente y puede apoyarse en implementación o fuentes durables, el gate no bloquea el avance.

## Una sola base de conocimiento

Cuando un proyecto utiliza una Wiki local y remota, evita mantener copias conceptualmente distintas para GitHub, Obsidian y agentes.

Una topología válida es:

```text
proyecto-wiki/
    Markdown canónico
        ↓
    GitHub versiona, cuando aplica
    Obsidian navega
    Project Orchestrator sintetiza
    coding agents leen sólo cuando corresponde
```

Obsidian es una interfaz sobre la memoria durable, no una fuente de verdad adicional.

## Starter mínimo para Wikis nuevas

El contenido real de `templates/wiki-starter/` es:

```text
proyecto-wiki/
├── 00-home.md
├── project-brief.md
├── AGENTS.md
├── status/
│   └── current-state.md
├── decisions/
│   └── README.md
└── sources/
    └── README.md
```

Cuando el proyecto necesita declarar formalmente su adopción, agrega `.ia-dos.yaml` desde `templates/adoption.template.yaml`. El manifiesto es opcional y no forma parte del starter físico.

La estructura es un punto de partida, no un esquema obligatorio para Wikis existentes. No renombres una memoria ya clara y navegable sólo para coincidir con estos nombres.

## Estructura por conocimiento

La Wiki no replica los Conversation Spaces `00–90`.

Los Conversation Spaces representan gobierno y autoridad. La Wiki organiza conocimiento reusable.

A medida que aparece contenido real, pueden surgir páginas como:

```text
product/financial-model.md
architecture/runtime.md
architecture/data-model.md
operations/deployment.md
decisions/single-writer.md
```

No crees carpetas vacías por anticipación.

## Páginas modulares

Prefiere páginas acotadas por tema en lugar de documentos monolíticos cuando el contenido pueda mantenerse y consumirse de forma independiente.

El objetivo no es maximizar fragmentación. Divide sólo cuando mejora mantenimiento o recuperación selectiva.

## Estado vigente primero

La Wiki responde principalmente:

> ¿Qué sabemos que es verdad ahora?

No debe narrar por defecto la historia completa de cómo se llegó a cada decisión.

La cronología detallada puede vivir en Git, Exchange, issues, ADRs u otros artefactos históricos.

Mantén explícita la diferencia entre:

- implementado;
- decidido o aprobado pero no implementado;
- pendiente;
- fuera de alcance;
- desconocido cuando corresponda.

Una decisión aceptada no demuestra implementación. La implementación sigue siendo autoridad para demostrar estado técnico real.

## Markdown portable

Usa características ampliamente compatibles:

- Markdown estándar;
- enlaces Markdown relativos;
- nombres de archivo descriptivos;
- rutas estables;
- YAML frontmatter mínimo sólo cuando aporte una función real.

Ejemplo de enlace canónico:

```md
[Estado actual](status/current-state.md)
```

Los wikilinks de Obsidian pueden ser útiles como conveniencia local, pero no deben ser necesarios para comprender o navegar la fuente canónica.

Los plugins de Obsidian tampoco deben contener semántica indispensable para agentes o lectores fuera de la aplicación.

## Mapa de memoria

En el starter, `00-home.md` actúa como punto de entrada humano y agéntico.

Su función es orientar hacia páginas concretas, no duplicar su contenido.

Una Wiki existente puede conservar otro nombre para su home si cumple la misma función.

## Lo que no vive por defecto en la Wiki

No guardes como memoria durable sólo porque exista:

- TASK completo;
- REPORT completo;
- logs;
- diffs;
- transcripciones;
- prompts;
- outputs de tests;
- backlog operativo.

Cuando un hecho descubierto en esos artefactos resulta durable, se sintetiza y se incorpora después de revisión.

## Consumo por coding agents

El coding agent no debe leer toda la Wiki por defecto.

Una `Execution Task` distingue:

### Contexto durable necesario

Extracto mínimo que el Orchestrator incluye porque la tarea lo necesita.

### Referencias Wiki

Rutas relacionadas para trazabilidad y navegación. Referenciar no significa leer.

### Lectura requerida

Documentos concretos que el coding agent sí debe consumir antes de ejecutar.

El modo habitual es que la tarea sea ejecutable con contexto mínimo seleccionado. La lectura directa de Wiki se reserva para cuando aporte precisión real.

Los hechos del repositorio que sean baratos de descubrir no necesitan duplicarse en `Contexto durable necesario`; ese bloque prioriza decisiones, restricciones y estado no obvio que condicionen la ejecución.

## Fallback cuando la Wiki no es accesible

Si el coding agent no puede acceder físicamente a la Wiki:

1. el Orchestrator selecciona los hechos vigentes necesarios;
2. los incluye en `Contexto durable necesario`;
3. conserva la referencia original cuando aporte trazabilidad;
4. no copia la Wiki completa.

Esto permite que IA-DOS funcione con coding agents que tengan capacidades de archivos diferentes.

## Rehidratación de conversaciones

Una nueva conversación de una Execution Cell debe poder recuperar contexto suficiente desde:

```text
memoria durable vigente
+
TASK actual
+
Exchange específico cuando aporte
```

No debería necesitar leer la conversación anterior completa.

Si el conocimiento indispensable sólo existe en ese chat anterior, el Memory Bootstrap Gate no está satisfecho.

## Gobierno de la memoria

El coding agent puede descubrir hechos durante una ejecución, pero no decide unilateralmente qué se convierte en memoria durable.

```text
Execution Report
    ↓ conocimiento potencialmente durable
Conversation Space revisa
    ↓
90 — Wiki y memoria, cuando aporta
    ↓
Wiki
```

Una Execution Cell como `Wiki Sync` puede encargarse de la modificación física o sincronización Git cuando sea necesario, mientras la síntesis de contenido permanece en el plano conversacional.

## Regla principal

```text
Wiki = estado durable reusable
Exchange = historial de instrucciones y retornos
Repositorio = implementación
Conversaciones = razonamiento y trabajo activo
```

Diseña la memoria para que estas fronteras sigan siendo visibles tanto para personas como para agentes.
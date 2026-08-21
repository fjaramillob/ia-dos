# Memoria durable portable y consumo desde Obsidian

IA-DOS distingue entre la responsabilidad de conservar conocimiento reusable y su posible materialización documental.

```text
memoria durable
= responsabilidad funcional

LLM Wiki
= materialización durable, portable y navegable
  de esa memoria para humanos y agentes
```

La LLM Wiki no es una transcripción de conversaciones ni una dependencia de una herramienta específica.

## Principio

Cuando un proyecto utiliza una LLM Wiki Markdown, debe ser:

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

Obsidian no se convierte en una fuente de verdad separada.

## Cuándo debe existir

No se crea por cantidad de mensajes ni por ceremonia.

Evalúa el [Memory Bootstrap Gate](memory-bootstrap-gate.md): si la siguiente Planning Task o Execution Task depende de conocimiento relevante que sólo vive en conversaciones, primero debe existir un checkpoint durable mínimo.

Si la tarea es autosuficiente y puede apoyarse en implementación o fuentes durables, el gate devuelve `PASS` y no exige crear una Wiki.

## Una sola base de conocimiento

Cuando un proyecto utiliza Markdown local y remoto, evita mantener copias conceptualmente distintas para GitHub, Obsidian y agentes.

Una topología válida es:

```text
LLM Wiki / Markdown canónico
    ↓
Git versiona, cuando aplica
Obsidian navega
Conversation Agent gobierna y selecciona contexto
coding agents leen sólo lo requerido
```

La ubicación puede ser un repositorio separado, documentación dentro de la app, un monorepo u otra estructura clara. IA-DOS no impone una topología física.

## Starter mínimo para Wikis nuevas

`templates/wiki-starter/` contiene:

```text
00-home.md
project-brief.md
AGENTS.md
status/current-state.md
decisions/README.md
sources/README.md
```

`.ia-dos.yaml` es opcional y se agrega sólo cuando el proyecto necesita una adopción reproducible.

No renombres una memoria existente y clara sólo para coincidir con el starter.

## Estructura por conocimiento

La Wiki no replica los Conversation Spaces `00–90`.

Los Conversation Spaces representan gobierno. La LLM Wiki organiza conocimiento reusable.

Crea páginas nuevas sólo cuando el contenido tenga suficiente entidad para mantenerse y consumirse de forma independiente. No anticipes carpetas vacías.

## Estado vigente primero

La LLM Wiki responde principalmente:

> ¿Qué sabemos que es verdad ahora?

Mantén explícita la diferencia entre:

- implementado;
- decidido o aprobado pero no implementado;
- pendiente;
- fuera de alcance;
- desconocido.

Una decisión aceptada no demuestra implementación. La implementación real sigue siendo autoridad para demostrar estado técnico.

## Markdown portable

Prefiere:

- Markdown estándar;
- enlaces relativos;
- nombres de archivo descriptivos;
- rutas estables;
- YAML frontmatter sólo cuando aporte una función real.

Los wikilinks y plugins de Obsidian pueden ser conveniencias locales, pero la semántica crítica no debe depender de ellos.

## Mapa de memoria

En el starter, `00-home.md` funciona como punto de entrada y mapa. Debe orientar hacia páginas concretas sin duplicarlas.

Una Wiki existente puede conservar otro nombre para su home si cumple esa función.

## Lo que no vive por defecto en la LLM Wiki

No guardes como memoria vigente:

- TASK completos;
- REPORT completos;
- logs;
- diffs;
- transcripciones;
- prompts;
- outputs de tests;
- backlog operativo.

Estos artefactos pueden aportar evidencia o historia. Si un hecho descubierto en ellos merece persistirse, primero se revisa y luego se sintetiza mediante una actualización autorizada.

## Consumo por coding agents

El coding agent no debe leer toda la LLM Wiki por defecto.

Una tarea distingue:

### Contexto durable necesario

Extracto mínimo incluido porque la tarea lo necesita directamente.

### Referencias Wiki

Rutas relacionadas para procedencia o navegación. Referenciar no significa leer.

### Lectura requerida

Documentos concretos que sí deben consumirse antes de actuar.

Los hechos técnicos baratos de descubrir no necesitan duplicarse en contexto durable. Ese bloque prioriza decisiones, restricciones y estado no obvio que condicionan la ejecución.

## Fallback cuando la Wiki no es accesible

Si el coding agent no puede acceder físicamente:

1. el Conversation Agent selecciona los hechos vigentes indispensables;
2. los incluye en la tarea;
3. conserva la referencia original cuando aporte trazabilidad;
4. no copia la Wiki completa;
5. declara la limitación.

## Rehidratación de conversaciones

Una conversación nueva de una Execution Cell debe poder recuperar contexto suficiente desde:

```text
LLM Wiki relevante
+ estado técnico actual
+ Execution Task o contrato operativo actual
+ delta vigente
```

Exchange específico puede aportar historial cuando sea útil, pero no sustituye ninguna de esas fuentes.

Si el conocimiento indispensable sólo existe en un chat anterior, el Memory Bootstrap Gate no está satisfecho.

## Gobierno de la memoria

El coding agent puede descubrir hechos durante una ejecución, pero el `Execution Report` sigue siendo evidencia, no un artefacto de consolidación de memoria.

```text
Coding Agent
→ Execution Report con hechos y evidencia observados

Cycle Owner + persona responsable, según autoridad
→ revisan el resultado
→ evalúan por separado qué hechos nuevos merecen memoria durable

Conversation Space / 90, cuando aporta
→ sintetiza el cambio documental

Execution Task documental autorizada
→ materializa la actualización de LLM Wiki
```

Si la propia Execution Task ya autoriza una actualización durable concreta con conocimiento confirmado, el coding agent puede materializarla dentro de ese alcance. Fuera de ese caso, no crea una sección de `conocimiento potencialmente durable` ni decide qué debe incorporarse.

Una Execution Cell como `Wiki Sync` puede encargarse de la modificación física o sincronización cuando exista un flujo durable que lo justifique. No se crea automáticamente por usar una Wiki.

## Fronteras

```text
LLM Wiki = conocimiento vigente reusable
Exchange = archivos intercambiados / historial cuando se conserva
Repository = implementación
Execution Report = evidencia de una ejecución
Conversations = razonamiento y gobierno activo
```

Diseña la memoria para que estas fronteras sigan visibles para personas y agentes.

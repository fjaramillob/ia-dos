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

## Prueba de continuidad entre agentes

La memoria es suficiente cuando un Coding Agent competente puede incorporarse en cualquier punto del desarrollo sin depender de conversaciones anteriores:

```text
repositorio real
+ LLM Wiki relevante
+ Task vigente
→ comprensión suficiente para contribuir
→ revalidación del estado real antes de modificar
```

La Wiki no reemplaza Git, runtime ni producción como evidencia. Debe decirle al nuevo agente qué espera encontrar, qué decisiones condicionan el trabajo y cuál fue el último baseline verificado.

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

## Memoria semántica y baseline operacional

IA-DOS separa dos necesidades que no deben confundirse.

### Memoria semántica

Conserva conocimiento durable que cambia cómo se comprende o desarrolla el proyecto: capacidades relevantes, contratos funcionales, arquitectura, datos, seguridad, sources of truth, decisiones, restricciones y estado del roadmap cuando corresponda.

Una Execution Task usa:

```text
Memory Policy: NONE | CONDITIONAL | REQUIRED
```

- `NONE`: no existe cambio semántico que justifique tocar la Wiki;
- `CONDITIONAL`: sólo se actualiza si ocurre un trigger explícito definido por el Cycle Owner;
- `REQUIRED`: la actualización semántica forma parte del outcome confirmado.

Pequeños outcomes pueden quedar sin actualización semántica y consolidarse después cuando, en conjunto, formen un cambio durable.

### Operational Baseline

Cuando un proyecto con Wiki publica software o cambia otro estado operacional relevante, la continuidad exige conservar el último baseline verificado aunque el cambio semántico sea `NONE`.

Debe permitir identificar, cuando aplique:

- repositorio y branch productiva;
- último HEAD remoto verificado;
- commit o versión realmente publicada;
- deployment, release o identificador equivalente;
- entorno y URL o endpoint canónico;
- estado observado;
- fecha de verificación.

```text
Repository HEAD
puede ser distinto de
Production Commit
```

Esa diferencia debe quedar visible. El baseline es un checkpoint durable; cada Coding Agent debe revalidar el remoto y el entorno antes de actuar.

No guardes dentro de la Wiki un `Wiki HEAD` autorreferente que obligue a un commit adicional sólo para registrar su propio SHA. El HEAD actual de la Wiki se obtiene del repositorio que la versiona.

### Historial de publicación

Cuando aporte continuidad, conserva un historial compacto de baselines publicados significativos: outcome, commit productivo, deployment/release, estado y fecha.

No copies cada commit ni cada ejecución. Git y la plataforma de delivery conservan el detalle exhaustivo.

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
+ Operational Baseline, cuando existe estado publicado
+ estado técnico actual revalidado
+ Execution Task o contrato operativo actual
+ delta vigente
```

Exchange específico puede aportar historial cuando sea útil, pero no sustituye ninguna de esas fuentes.

Si el conocimiento indispensable sólo existe en un chat anterior, el Memory Bootstrap Gate no está satisfecho.

## Gobierno de la memoria

El Conversation Space y la persona responsable conservan dirección. El Coding Agent no decide roadmap o prioridades por inferir que algo “merece documentación”.

El Cycle Owner define dentro de la Task:

- `Memory Policy`;
- triggers, si es `CONDITIONAL`;
- rutas y fuentes autorizadas;
- si el baseline operacional debe actualizarse por publicación;
- si corresponde historia compacta de release.

Cuando la misma frontera de autoridad cubre implementación, Git, delivery y Wiki, el Coding Agent puede completar todo dentro del mismo outcome:

```text
Implement
→ Verify
→ Commit / Push
→ Deploy / Smoke
→ actualizar memoria autorizada
→ actualizar Operational Baseline
→ Execution Report
```

Una Task de Wiki separada se usa cuando el resultado principal es:

- un bootstrap requerido por `Memory Bootstrap Gate`;
- consolidar varios outcomes menores;
- reparar memoria inconsistente u obsoleta;
- realizar una migración/reorganización documental;
- trabajar bajo una frontera de autoridad distinta.

No la crees como ritual posterior a cada ejecución.

El Execution Report registra qué ocurrió, incluido `Durable Memory Impact` y el estado del `Operational Baseline`. No sustituye la Wiki ni la aprobación del Cycle Owner.

## Fronteras

```text
LLM Wiki = conocimiento vigente reusable
Exchange = archivos intercambiados / historial cuando se conserva
Repository = implementación
Execution Report = evidencia de una ejecución
Conversations = razonamiento y gobierno activo
```

Diseña la memoria para que estas fronteras sigan visibles para personas y agentes.

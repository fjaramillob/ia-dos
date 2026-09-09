# Compresión de contexto por autoridad

Este contrato reduce repetición sin perder control, seguridad ni continuidad.

## Principio

No repitas contexto estable cuando ya exista en una fuente durable, vigente y accesible. Cada artefacto operativo debe transportar sólo:

```text
referencias de autoridad
+ delta del ciclo
+ contrato operativo explícito
```

La compresión correcta elimina duplicación. No elimina hechos indispensables, permisos, límites, criterios ni condiciones de detención.

`Autocontenida` no significa copiar la historia completa del proyecto.

## Precondición: memoria suficiente

La compresión por referencia sólo funciona cuando el conocimiento que se pretende omitir ya existe en una fuente durable adecuada.

Si la siguiente unidad depende de decisiones, estado o contexto que sólo viven en conversaciones, aplica primero el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md).

```text
PASS
→ comprime usando fuentes durables y delta

BOOTSTRAP REQUIRED
→ persiste el checkpoint mínimo antes de depender de referencias
```

## Tres capas operativas

### 1. Embedded Contract

Debe viajar dentro de la Task porque forma parte de su autoridad concreta.

Incluye siempre lo necesario de:

- Artifact Type y Destination Role;
- Cycle ID y Task ID;
- Cycle Owner y destino del retorno;
- outcome;
- alcance y fuera de alcance;
- Authority Envelope y acceso permitido;
- seguridad y datos;
- criterios de aceptación;
- verificaciones;
- condiciones de detención;
- salida esperada y salida prohibida.

Nunca relegues permisos, secretos, acciones externas, costes, producción o límites de seguridad únicamente a una referencia indirecta.

### 2. Required Reading

Documentos concretos que el receptor debe leer porque contienen contexto vigente indispensable que no conviene duplicar.

Ejemplos:

- una decisión durable específica;
- un contrato técnico vigente;
- una instrucción local `AGENTS.md`;
- un Implementation Plan revisado cuando su contenido sigue siendo indispensable para ejecutar.

`Required Reading` implica lectura obligatoria antes de actuar.

### 3. Reference

Referencia de autoridad, trazabilidad o navegación. No implica lectura por defecto.

Puede incluir:

- procedencia de una decisión;
- páginas Wiki relacionadas;
- PR o reporte previo;
- versión o commit que permite auditar el origen.

## Delta del ciclo

Viaja en cada artefacto porque describe qué cambió desde la última fuente o artefacto válido:

- decisión nueva o modificada;
- evidencia recién observada;
- bloqueo resuelto o aparecido;
- objetivo exacto de la tarea;
- trabajo que debe preservarse;
- desconocidos que siguen abiertos;
- artefacto previo que gobierna la continuidad.

El delta no vuelve a narrar la historia completa.

## Criterio de autosuficiencia

Una Task es suficientemente autocontenida cuando:

```text
Task
+ Required Reading declarado
→ permiten ejecutarla correctamente sin depender de conversaciones previas
```

No repitas por rutina:

- Implementation Plan completo;
- Wiki completa;
- reportes previos completos;
- contrato factual completo;
- historia del proyecto.

Si una pieza debe ser leída, declárala como `Required Reading`. Si sólo aporta procedencia, declárala como `Reference`. Si define autoridad o límites de la Task, embébela.

## Contrato mínimo de compresión

Toda Planning Task, Environment Preflight, Execution Task o Execution Resume debe poder distinguir:

```text
FUENTES DE AUTORIDAD
- [RECURSO O DOCUMENTO]: [ÁMBITO QUE GOBIERNA]

ARTEFACTO PREVIO VÁLIDO
- [REFERENCIA O NO APLICA]

DELTA DEL CICLO
- [CAMBIO, DECISIÓN, EVIDENCIA O BLOQUEO RELEVANTE]

EMBEDDED CONTRACT
- [OUTCOME, PERMISOS, LÍMITES, CRITERIOS Y DETENCIONES]

REQUIRED READING
- [DOCUMENTOS CONCRETOS O NINGUNO]

REFERENCES
- [TRAZABILIDAD/NAVEGACIÓN O NINGUNA]
```

## Gate de compresión

Antes de emitir un bloque operativo, pregunta:

```text
1. ¿Este dato ya existe en una fuente durable accesible y vigente?
2. ¿El receptor necesita leer su contenido o basta una referencia precisa?
3. ¿El dato pertenece al delta actual?
4. ¿Es autoridad, permiso, límite o condición que debe permanecer embebida?
```

Resultado:

- lectura indispensable → `Required Reading`;
- sólo procedencia/navegación → `Reference`;
- cambio actual → delta;
- permiso, límite, criterio o detención → Embedded Contract;
- fuente no accesible → incluye sólo el extracto indispensable;
- conocimiento reusable aún no durable → evalúa Memory Bootstrap Gate;
- contradicción o vigencia dudosa → detente y resuelve autoridad antes de compactar.

## Compatibilidad terminológica

Las plantillas o proyectos existentes pueden usar:

```text
Contexto durable necesario
≈ extracto embebido indispensable

Lectura requerida
= Required Reading

Referencias Wiki
⊂ Reference
```

Las nuevas superficies deben favorecer `Embedded Contract`, `Required Reading` y `Reference` porque distinguen con mayor claridad qué viaja, qué debe leerse y qué sólo sirve de trazabilidad.

## Fallback autosuficiente

Cuando una fuente requerida existe pero el coding agent no puede accederla:

1. declara la limitación;
2. incluye sólo el extracto indispensable dentro del Embedded Contract;
3. identifica la fuente original;
4. no presenta el extracto como una nueva autoridad independiente;
5. evita copiar repositorios, Wikis o documentos completos.

Este fallback resuelve una limitación de acceso de la tarea actual. No convierte una conversación en memoria durable.

## Wiki y memoria durable

IA-DOS no exige una Wiki independiente. Cuando el proyecto sí tiene una Wiki o memoria durable equivalente:

- úsala como autoridad para contexto estable dentro de su ámbito;
- mantén allí decisiones aceptadas y estado confirmado;
- no registres propuestas como implementación;
- referencia documentos concretos, no sólo la raíz de la Wiki;
- incluye fecha, versión o commit cuando la vigencia pueda ser ambigua;
- no obligues al coding agent a leer la Wiki completa.

La implementación sigue siendo autoridad para el estado técnico real. La memoria durable explica decisiones y contexto; no sustituye código, configuración, pruebas o despliegues.

## Antipatrones

- copiar la memoria completa en cada tarea;
- copiar un Implementation Plan completo sólo por rutina;
- escribir `ver Wiki` sin rutas ni ámbito;
- tratar toda referencia como lectura obligatoria;
- omitir permisos porque aparecen en otro documento;
- depender de memoria conversacional no durable;
- repetir el mismo contexto chat-only en muchas tareas en vez de persistirlo cuando ya es reusable;
- convertir el delta en un resumen completo del proyecto;
- asumir que una Wiki demuestra estado implementado;
- compactar una contradicción sin resolver autoridad.

## Regla principal

```text
Embedded Contract
+ Required Reading
+ Reference
+ delta vigente
```

permiten reducir repetición sin delegar autoridad por accidente. Menos contexto no significa menos control.
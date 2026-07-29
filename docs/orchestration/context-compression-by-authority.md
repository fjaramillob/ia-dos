# Compresión de contexto por autoridad

Este contrato reduce repetición sin perder control, seguridad ni continuidad.

## Principio

No repitas contexto estable cuando ya exista en una fuente durable, vigente y accesible. Cada artefacto operativo debe transportar solo:

```text
referencias de autoridad
+ delta del ciclo
+ contrato de ejecución
```

La compresión correcta elimina duplicación. No elimina hechos indispensables, permisos, límites, criterios ni condiciones de detención.

## Tres capas de contexto

### 1. Contexto durable

Vive en la fuente designada como memoria durable del proyecto. Puede incluir:

- propósito y alcance aceptados;
- decisiones vigentes;
- glosario;
- arquitectura aprobada;
- roles de repositorios y servicios;
- guardrails estables;
- convenciones durables;
- estado conocido que tenga evidencia y fecha.

No debe copiarse completo en cada Planning Task o Execution Task. Debe referenciarse mediante recurso, ruta o identificador estable.

### 2. Delta del ciclo

Viaja en cada artefacto porque describe qué cambió desde la última fuente o artefacto válido:

- decisión nueva o modificada;
- evidencia recién observada;
- bloqueo resuelto o aparecido;
- objetivo exacto de la tarea;
- trabajo que debe preservarse;
- desconocidos que siguen abiertos;
- artefacto previo que gobierna la continuidad.

El delta no vuelve a narrar la historia completa.

### 3. Contrato operativo

Siempre debe quedar explícito en la tarea concreta:

- Artifact Type y Destination Role;
- Cycle ID y Task ID;
- Cycle Owner y destino del retorno;
- objetivo único;
- fuentes obligatorias y autoridad;
- acceso permitido;
- zonas autorizadas y prohibidas;
- capacidades y autorizaciones;
- criterios de aceptación;
- verificaciones;
- condiciones de detención;
- salida esperada y salida prohibida.

Nunca relegues permisos, secretos, acciones externas, costes, producción o límites de seguridad únicamente a una referencia indirecta.

## Contrato mínimo

Toda Planning Task, Environment Preflight, Execution Task o Execution Resume debe incluir:

```text
FUENTES DE AUTORIDAD
- [RECURSO O DOCUMENTO]: [ÁMBITO QUE GOBIERNA]

ARTEFACTO PREVIO VÁLIDO
- [REFERENCIA O NO APLICA]

DELTA DEL CICLO
- [CAMBIO, DECISIÓN, EVIDENCIA O BLOQUEO RELEVANTE]

CONTRATO OPERATIVO
- [OBJETIVO, PERMISOS, LÍMITES, CRITERIOS Y DETENCIONES]
```

## Gate de compresión

Antes de emitir un bloque operativo, pregunta:

```text
1. ¿Este dato ya existe en una fuente durable accesible y vigente?
2. ¿El receptor necesita el contenido completo o basta una referencia precisa?
3. ¿El dato pertenece al delta actual?
4. ¿Es un permiso, límite o condición que debe permanecer explícito?
```

Resultado:

- fuente durable accesible y vigente: referencia;
- cambio actual: incluir como delta;
- permiso, límite, criterio o detención: incluir explícitamente;
- fuente no accesible o insuficiente: incluir un extracto autosuficiente;
- contradicción o vigencia dudosa: detener y resolver autoridad antes de compactar.

## Fallback autosuficiente

Una tarea debe seguir siendo ejecutable cuando el coding agent no pueda leer la fuente durable.

En ese caso:

1. declara que la referencia no es accesible;
2. incluye solo el extracto indispensable;
3. identifica la fuente original;
4. no presenta el extracto como una nueva autoridad independiente;
5. evita copiar repositorios, Wikis o documentos completos.

## Wiki y memoria durable

IA-DOS no exige una Wiki independiente. Cuando el proyecto sí tiene una Wiki o memoria durable equivalente:

- úsala como autoridad para contexto estable;
- mantén allí decisiones aceptadas y estado confirmado;
- no registres propuestas como implementación;
- actualízala cuando el conocimiento sea durable y tenga evidencia;
- referencia documentos concretos, no solo la raíz de la Wiki;
- incluye fecha, versión o commit cuando la vigencia pueda ser ambigua.

La implementación sigue siendo autoridad para el estado técnico real. La memoria durable explica decisiones y contexto; no sustituye código, configuración, pruebas o despliegues.

## Medición de eficiencia

La eficiencia no se evalúa solo por longitud. Una tarea compacta es mejor cuando conserva precisión y reduce repetición.

Registra cuando sea útil:

- cantidad de fuentes referenciadas;
- bloques durables omitidos por referencia;
- tamaño aproximado del delta;
- aclaraciones posteriores causadas por contexto insuficiente;
- re-trabajo provocado por referencias ambiguas o desactualizadas.

No optimices tokens a costa de corrección, seguridad o trazabilidad.

## Antipatrones

- copiar la memoria completa en cada tarea;
- escribir “ver Wiki” sin rutas ni ámbitos;
- omitir permisos porque aparecen en otro documento;
- depender de memoria conversacional no durable;
- incluir historial irrelevante por precaución;
- convertir el delta en un resumen completo del proyecto;
- asumir que una Wiki demuestra estado implementado;
- compactar una contradicción sin resolver autoridad.

## Regla principal

La fuente durable conserva el contexto estable. El artefacto operativo transporta referencias precisas, el delta vigente y un contrato explícito. Menos repetición nunca significa menos control.
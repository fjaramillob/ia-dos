# Autoridad de fuentes, artefactos y entornos

IA-DOS no presupone una topología concreta de carpetas, repositorios, servicios o herramientas. Antes de planificar o ejecutar, cada recurso real debe declarar su función y autoridad.

## Contrato mínimo por recurso

| Recurso | Rol | Autoridad para | Acceso permitido | Limitaciones |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[LÍMITES]` |

El recurso puede ser un repositorio, carpeta, documento, Wiki, base de datos, servicio, entorno remoto, issue, pull request, dataset u otro artefacto disponible.

## Roles frecuentes

### Método

Define cómo organizar, planificar, ejecutar, verificar y reportar. IA-DOS normalmente cumple este rol y se consulta en solo lectura durante el trabajo de otros proyectos.

### Memoria durable

Conserva decisiones aceptadas, contexto, arquitectura vigente y estado conocido. No demuestra por sí sola que algo esté implementado.

### Implementación

Demuestra el estado real del producto mediante código, configuración, migraciones, pruebas, datos o artefactos desplegados.

### Evidencia y trazabilidad

Conserva tareas, diffs, reportes, pruebas, decisiones, revisiones y estados verificables.

### Referencia

Aporta antecedentes, patrones o aprendizaje. No gobierna automáticamente el resultado actual y permanece en solo lectura salvo autorización explícita.

## Authority Envelope

La `Execution Task` es la autoridad concreta de una ejecución. Puede incluir un `Authority Envelope` que agrupe permisos explícitos para el outcome completo sin crear un Artifact Type nuevo.

Ejemplo semántico:

```text
Authority Envelope

Code:
- escritura autorizada en scope

Git:
- stage selectivo
- commit
- push fast-forward

Delivery:
- deployment mediante mecanismo existente

Production:
- smoke autorizado

No autorizado:
- schema
- nuevos servicios
- costes
- force push
- cambios fuera del scope
```

Reglas:

```text
acción sensible no declarada
→ no autorizada

acción explícitamente declarada en la Task
+ gates previos cumplidos
+ frontera estable
→ puede ejecutarse sin otra ida y vuelta humana por rutina

cambio material de outcome, scope, autoridad, arquitectura,
seguridad, datos, riesgo, coste o entorno
→ STOP y nueva decisión
```

El Authority Envelope no permite al coding agent aprobar su propio plan o ejecución.

## Capacidades separadas, una sola frontera

Lectura, escritura, branch, commit, push, PR, merge, despliegue, producción, datos, servicios externos y costes siguen siendo capacidades separadas. Que sean separadas no significa que requieran Tasks separadas.

Pueden formar parte de la misma Execution Task cuando:

- sirven al mismo outcome cohesivo;
- están explícitamente autorizadas;
- los gates previos se cumplieron;
- la frontera de autoridad permanece estable.

No impongas una nueva aprobación humana entre fases sólo por rutina si esa autoridad ya fue delegada explícitamente en la Task.

## Compresión de contexto

Aplica `docs/orchestration/context-compression-by-authority.md`.

Cada artefacto operativo debe distinguir:

```text
fuentes de autoridad
+ artefacto previo válido
+ delta del ciclo
+ Embedded Contract
+ Required Reading
+ References
```

- el contexto estable se referencia cuando la fuente es accesible y vigente;
- el cambio actual viaja como delta;
- permisos, límites, criterios y condiciones de detención permanecen explícitos;
- cuando una fuente no es accesible, incluye sólo el extracto indispensable y conserva su referencia original.

Una referencia genérica como `ver Wiki` no es suficiente. Usa documento, ruta, versión, commit o identificador estable y declara qué ámbito gobierna.

## Contradicciones

Cuando dos fuentes discrepan:

1. identifica el tipo de información en conflicto;
2. determina qué recurso tiene autoridad para ese ámbito;
3. no resuelvas la contradicción copiando ambas versiones;
4. registra la decisión en la fuente durable correspondiente cuando aplique;
5. escala al Cycle Owner o a `00` cuando exceda la autoridad del espacio actual.

No compactes contexto contradictorio. Resuelve primero la autoridad y la vigencia.

## Readiness del entorno

Antes de una Execution Task comprueba sólo las precondiciones indispensables para las capacidades que realmente utilizará:

- entorno disponible: local, remoto o combinado;
- recursos accesibles;
- fuentes faltantes;
- estado que debe preservarse;
- permisos reales;
- secretos o datos que no deben exponerse;
- acciones externas o con coste que requieren autorización.

Planning y Environment Preflight continúan siendo de solo lectura respecto del proyecto/entorno inspeccionados.

## No imponer topología

No impongas:

- una carpeta raíz específica;
- repositorios separados;
- una Wiki independiente;
- Exchange;
- GitHub;
- trabajo local;
- una herramienta, proveedor o stack concreto.

## Regla principal

La estructura del proyecto pertenece al proyecto. IA-DOS gobierna el contrato de autoridad, acceso, evidencia, compresión y retorno.

Una acción sensible no declarada no está autorizada. Una acción explícitamente declarada dentro de una frontera estable no necesita una nueva ceremonia sólo porque ocurre en una fase posterior de la misma Task.
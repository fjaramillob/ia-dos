# Execution Task

Consulta:

- `docs/execution/execution-task-types.md`;
- `docs/execution/source-and-artifact-authority.md`;
- `docs/orchestration/agent-role-and-artifact-loop.md`;
- `docs/orchestration/typed-artifact-routing.md`.

## Encabezado obligatorio

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar alcance | aprobar el propio resultado | iniciar otra unidad
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID]
```

El mecanismo de transporte o almacenamiento no cambia este contrato. Si el proyecto usa Exchange, Exchange sólo almacena o pone a disposición el `.md` ya construido y no genera ni modifica IDs, estados o permisos.

## Precondiciones de emisión

Antes de emitir la tarea confirma:

- [ ] el resultado está definido, es pequeño y verificable;
- [ ] `Memory Bootstrap Gate = PASS | NO APLICA`;
- [ ] readiness indispensable = `LISTO PARA EJECUCIÓN | NO APLICA`;
- [ ] Planning previo = `[REFERENCIA REVISADA | NO APLICA]`;
- [ ] las decisiones humanas indispensables para esta unidad están resueltas;
- [ ] la tarea puede completarse, verificarse y reportarse como una sola unidad.

Si alguna precondición necesaria no se cumple, no autorices escritura.

## Identificación

- Cycle ID: `[CYCLE-ID O NO APLICA]`
- ID: `[TASK-ID]`
- Título: `[TÍTULO BREVE]`
- Estado: `Propuesta | Autorizada | En ejecución | Bloqueada | Completada | Cancelada`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino del Execution Report: `[CONVERSATION SPACE]`
- Espacio de escalamiento: `[NORMALMENTE 00 — DIRECCIÓN Y ORQUESTACIÓN]`
- Tipo principal: `[INSPECT | BOOTSTRAP | BUILD | FIX | REFACTOR | MIGRATE | TEST | HARDEN | DOCUMENT | WIKI | RELEASE | OPERATE]`
- Tipo secundario inseparable: `[TIPO O NINGUNO]`
- Responsable humano: `[ROL O PERSONA]`
- Coding agent o entorno: `[ROL O HERRAMIENTA DISPONIBLE]`
- Execution Cell o sesión: `[NOMBRE O NO APLICA]`
- Rol activo: `Coding Agent — Execution`
- Implementation Plan revisado: `[REFERENCIA O NO APLICA]`
- Environment Readiness Report: `[REFERENCIA LISTO PARA EJECUCIÓN O NO APLICA]`
- Acceso a IA-DOS: `Embedded Contract | Remote Repository | Local Reference`
- Referencia local de IA-DOS: `[RUTA O NO DISPONIBLE]`

Una Execution Cell conserva continuidad, pero no sustituye el rol receptor, el Cycle Owner ni las autorizaciones de esta tarea.

## Contrato de sesión o célula

Cuando el proyecto use una Execution Cell persistente, reutiliza la conversación activa mientras siga respondiendo bien.

No renueves por edad, tiempo, mensajes o cantidad de tareas. Reutilizar la conversación no reutiliza permisos.

Planning y Execution conservan autorizaciones separadas, pero esa separación no exige una conversación de ejecución nueva.

## Objetivo

Describe un único resultado concreto, terminable y verificable.

## Contexto durable necesario

Incluye únicamente decisiones, restricciones y estado no obvio que el coding agent necesita directamente.

No copies toda la historia del proyecto.

## Referencias Wiki

- `[RUTA O REFERENCIA PARA TRAZABILIDAD]`

No implican lectura automática.

## Lectura requerida

- `[DOCUMENTO CONCRETO O NINGUNA]`

## Autoridad de fuentes, artefactos y entornos

| Recurso | Rol | Autoridad para | Acceso permitido | Limitaciones |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[LÍMITES]` |

Incluye instrucciones locales aplicables, por ejemplo `AGENTS.md` o equivalente.

## Acceso al método

La tarea debe ser autosuficiente.

- usa contrato embebido cuando aporte;
- consulta fuente remota cuando esté disponible;
- usa referencia local compartida cuando haya sido declarada;
- no clones IA-DOS dentro del producto;
- no crees una referencia local sin autorización.

Una topología local posible, no obligatoria, es:

```text
Proyectos/
├── 00-ia-dos/
└── [Proyecto]/
    ├── [implementación]/
    ├── [memoria, si existe]/
    └── [exchange, si existe]/
```

## Readiness del entorno

- Entorno: `[LOCAL / REMOTO / COMBINADO / OTRO]`
- Estado: `LISTO PARA EJECUCIÓN | NO APLICA`
- Evidencia o reporte: `[REFERENCIA]`
- Estado que debe preservarse: `[DETALLE]`
- Accesos o secretos no disponibles: `[NINGUNO O DETALLE NO SENSIBLE]`

No inventes rutas, credenciales, herramientas o permisos.

## Problema o evidencia inicial

Describe qué ocurre hoy y qué evidencia lo confirma.

## Alcance

### Incluido

- `[CAMBIO O ANÁLISIS AUTORIZADO]`

### Fuera de alcance

- `[CAMBIO NO AUTORIZADO]`

## Zonas autorizadas

- recursos o artefactos modificables: `[LISTA]`
- rama o modo de trabajo: `[RAMA / SOLO LECTURA / MODIFICACIÓN LOCAL / OTRO]`
- rutas o áreas permitidas:
  - `[RUTA O ÁREA]`
- rutas o áreas prohibidas:
  - `[RUTA O ÁREA]`

## Capacidades y autorizaciones

- Lectura: `Autorizada | No autorizada`
- Escritura: `Autorizada | No autorizada`
- Crear branch: `Autorizado | No autorizado | No aplica`
- Commit: `Autorizado | No autorizado | No aplica`
- Push: `Autorizado | No autorizado | No aplica`
- Pull request: `Autorizado | No autorizado | No aplica`
- Merge: `Autorizado | No autorizado | No aplica`
- Despliegue o producción: `Autorizado | No autorizado | No aplica`
- Datos, recursos externos o costes: `[AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]`

## Guardrails de rol

- no actuar como `00` ni Project Orchestrator;
- no cambiar Cycle Owner, objetivo o destino;
- no aprobar el propio resultado;
- no iniciar otra unidad;
- no ampliar alcance;
- respetar autoridad de cada recurso;
- cumplir instrucciones locales;
- no modificar secretos o datos sensibles;
- no cambiar arquitectura, dependencias o seguridad salvo alcance explícito;
- preservar comportamiento y trabajo no relacionados;
- detenerse ante contradicciones relevantes;
- no afirmar verificación sin evidencia;
- no continuar cuando aparezcan objetivos independientes.

## Criterios de aceptación

- [ ] `[RESULTADO OBSERVABLE]`

## Pruebas y verificaciones

- `[COMANDO, REVISIÓN O PROCEDIMIENTO]`

Declara la evidencia esperada.

## Condiciones de detención

Detente y reporta cuando:

- falte información crítica;
- exista trabajo previo no identificado que pueda perderse;
- aparezca una instrucción local aplicable no declarada;
- sea necesario tocar recursos o usar capacidades no autorizadas;
- falle una verificación crítica;
- aparezca riesgo de seguridad, pérdida de datos o coste;
- sea necesaria una decisión no confirmada;
- el tipo declarado ya no represente el trabajo;
- aparezcan varios resultados independientes;
- una precondición de memoria o readiness deje de cumplirse.

## Documentación y memoria

- artefactos técnicos a actualizar: `[LISTA O NINGUNO]`
- conocimiento durable que la propia tarea autoriza registrar: `[HECHOS/DECISIONES CONFIRMADOS O NINGUNO]`
- ADR o equivalente requerido: `Sí | No`

Si la tarea no autoriza una actualización durable concreta, el coding agent sólo reporta hechos y evidencia; la evaluación de memoria ocurre después de revisar el reporte.

## Encabezado de retorno obligatorio

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión de evidencia bajo la autoridad aplicable
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

## Entrega requerida

Devuelve:

- resultado observable;
- recursos revisados y modificados;
- instrucciones y fuentes consultadas;
- pruebas, verificaciones y evidencia;
- autorizaciones utilizadas;
- fuera de alcance preservado;
- desviaciones o problemas;
- pendientes del alcance original;
- condiciones de detención activadas;
- atención concreta requerida o `Ninguna`.

El coding agent no determina la decisión de gobierno posterior, no consolida memoria durable salvo autorización explícita de la propia tarea y no inicia otra unidad.

## Autoridad posterior

El Cycle Owner revisa dentro de la autoridad delegada. La persona responsable conserva la aprobación final cuando la decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

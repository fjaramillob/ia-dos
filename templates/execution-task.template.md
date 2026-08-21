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

El mecanismo de transporte o almacenamiento no cambia este contrato. Si el proyecto usa Exchange, Exchange sólo almacena o pone a disposición el `.md` ya construido; no genera ni modifica `Task ID`, `Cycle ID`, estados o permisos.

## Identificación

- Cycle ID: `[CYCLE-ID O NO APLICA]`
- ID: `[TASK-ID]`
- Título: `[TÍTULO BREVE]`
- Estado: `Propuesta | Aprobada | En ejecución | Bloqueada | Completada | Cancelada`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino del Execution Report: `[CONVERSATION SPACE]`
- Espacio de escalamiento: `[NORMALMENTE 00 — DIRECCIÓN Y ORQUESTACIÓN]`
- Tipo de ejecución principal: `[INSPECT | BOOTSTRAP | BUILD | FIX | REFACTOR | MIGRATE | TEST | HARDEN | DOCUMENT | WIKI | RELEASE | OPERATE]`
- Tipo secundario, solo si es inseparable: `[TIPO O NINGUNO]`
- Responsable humano: `[ROL O PERSONA]`
- Coding agent o entorno: `[ROL O HERRAMIENTA DISPONIBLE]`
- Execution Cell o sesión independiente: `[NOMBRE O NO APLICA]`
- Rol activo: `Coding Agent — Execution`
- Implementation Plan aprobado: `[REFERENCIA O NO APLICA]`
- Acceso a IA-DOS: `Embedded Contract | Remote Repository | Local Reference`
- Referencia local de IA-DOS: `[RUTA O NO DISPONIBLE]`

Incluye `templates/agent-role-contract.template.md` como contrato embebido cuando corresponda.

El tipo clasifica el trabajo, pero no concede permisos. Una Execution Cell conserva continuidad operacional, pero no sustituye el rol receptor, el Cycle Owner ni las autorizaciones de esta tarea.

## Contrato de sesión o célula

La frontera de autorización entre planificación y ejecución debe ser explícita.

Cuando el proyecto use una `Execution Cell` persistente, puede reutilizar la conversación activa de esa célula para múltiples Execution Tasks mientras siga respondiendo bien. Reutilizar la conversación no reutiliza permisos de tareas anteriores.

Cuando el proyecto use sesiones independientes, no reutilices una sesión de planificación como si ya tuviera autorización de ejecución.

La política de persistencia de conversaciones de planificación permanece separada de este contrato y no se resuelve por esta plantilla.

## Objetivo

Describe un único resultado concreto, terminable y verificable.

## Gate de tamaño

Confirma:

- [ ] la tarea no mezcla resultados independientes;
- [ ] puede completarse, verificarse y reportarse como una sola unidad;
- [ ] las dependencias previas están resueltas;
- [ ] no contiene fases que deban aprobarse por separado.

Cuando alguna respuesta sea negativa, divide la tarea antes de ejecutarla.

## Contexto mínimo

- decisiones aceptadas;
- evidencia inicial;
- fuentes obligatorias;
- restricciones no negociables;
- trabajo previo que debe preservarse;
- desconocidos que no bloquean la ejecución.

No copies toda la historia del proyecto.

## Autoridad de fuentes, artefactos y entornos

| Recurso | Rol | Autoridad para | Acceso permitido | Limitaciones |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[LÍMITES]` |

Incluye las instrucciones locales aplicables del repositorio o entorno, por ejemplo `AGENTS.md`, archivos equivalentes, convenciones de contribución o políticas técnicas. Si no existen, decláralo.

## Acceso al método

La tarea debe ser autosuficiente.

- usa el contrato embebido cuando corresponda;
- consulta la fuente remota cuando esté disponible;
- usa una referencia local compartida cuando haya sido declarada;
- no clones IA-DOS dentro del repositorio del producto;
- no realices un clon silencioso;
- solicita autorización antes de crear una referencia local.

Una configuración local válida, no obligatoria, es:

```text
Proyectos/
├── 00-ia-dos/
└── [Proyecto]/
    ├── [proyecto-app]/
    ├── [proyecto-wiki]/
    └── [proyecto-exch]/
```

## Readiness del entorno

- Entorno: `[LOCAL / REMOTO / COMBINADO / OTRO]`
- Recursos disponibles: `[LISTA]`
- Recursos faltantes: `[LISTA O NINGUNO]`
- Estado que debe preservarse: `[DETALLE]`
- Accesos o secretos no disponibles: `[DETALLE]`

No inventes rutas, credenciales, herramientas ni permisos.

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
- Crear branch o equivalente: `Autorizado | No autorizado | No aplica`
- Commit o versión: `Autorizado | No autorizado | No aplica`
- Push o cambio remoto: `Autorizado | No autorizado | No aplica`
- Pull request o revisión remota: `Autorizado | No autorizado | No aplica`
- Merge o integración final: `Autorizado | No autorizado | No aplica`
- Despliegue o producción: `Autorizado | No autorizado | No aplica`
- Datos, recursos externos o costes: `[AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]`

## Guardrails de rol

- no actuar como `00` ni como Project Orchestrator;
- no cambiar Cycle Owner, objetivo o destino;
- no aprobar el propio resultado;
- no iniciar otra unidad;
- no ampliar alcance sin aprobación;
- respetar la autoridad de cada recurso;
- cumplir las instrucciones locales aplicables;
- no modificar secretos ni datos sensibles;
- no cambiar arquitectura, dependencias o seguridad salvo alcance explícito;
- preservar comportamiento y trabajo no relacionados;
- detenerse ante contradicciones con fuentes o estado real;
- no afirmar verificación sin evidencia;
- no continuar cuando la tarea revele objetivos independientes adicionales.

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
- sea necesario tocar recursos no autorizados;
- falle una verificación crítica;
- aparezca un riesgo de seguridad, pérdida de datos o coste;
- sea necesaria una decisión no confirmada;
- el tipo declarado ya no represente el trabajo;
- la tarea revele varios resultados independientes;
- se requiera crear o clonar una referencia local no autorizada.

## Documentación y memoria

- artefactos técnicos a actualizar: `[LISTA O NINGUNO]`
- conocimiento durable que la propia tarea autoriza registrar: `[DECISIONES O NINGUNO]`
- ADR o equivalente requerido: `Sí | No`

No registres propuestas como estado implementado. Si la tarea no autoriza una actualización durable concreta, el coding agent sólo reporta hechos y evidencia; el Cycle Owner evaluará después qué merece consolidarse.

## Encabezado de retorno obligatorio

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión y decisión del Cycle Owner
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Execution Cell o sesión independiente: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

## Entrega requerida

El coding agent debe devolver un `Execution Report` al destino declarado, incluyendo:

- resultado observable;
- recursos revisados y modificados;
- instrucciones locales consultadas;
- pruebas, verificaciones y evidencia;
- autorizaciones utilizadas;
- fuera de alcance preservado;
- desviaciones o problemas;
- pendientes del alcance original;
- condiciones de detención activadas;
- cualquier atención concreta que requiera revisión del Cycle Owner.

El coding agent no determina la decisión de gobierno posterior, no consolida memoria durable salvo autorización explícita de la propia tarea y no inicia automáticamente el siguiente ciclo o tarea.
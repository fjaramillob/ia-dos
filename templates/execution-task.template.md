# Execution Task

Consulta:

- `docs/execution/execution-task-types.md`;
- `docs/execution/source-and-artifact-authority.md`.

## Identificación

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
- Implementation Plan aprobado: `[REFERENCIA O NO APLICA]`

El tipo clasifica el trabajo, pero no concede permisos.

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

## Guardrails

- no ampliar alcance sin aprobación;
- respetar la autoridad de cada recurso;
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
- sea necesario tocar recursos no autorizados;
- falle una verificación crítica;
- aparezca un riesgo de seguridad, pérdida de datos o coste;
- sea necesaria una decisión no confirmada;
- el tipo declarado ya no represente el trabajo;
- la tarea revele varios resultados independientes.

## Documentación y memoria

- artefactos técnicos a actualizar: `[LISTA O NINGUNO]`
- conocimiento durable que debe registrarse: `[DECISIONES O NINGUNO]`
- ADR o equivalente requerido: `Sí | No`

No registres propuestas como estado implementado.

## Entrega requerida

El coding agent debe devolver un `Execution Report` al destino declarado, incluyendo:

- resultado observable;
- recursos revisados y modificados;
- pruebas y evidencia;
- autorizaciones utilizadas;
- fuera de alcance respetado;
- desviaciones, riesgos y decisiones pendientes;
- estado del entorno y del control de versiones;
- actualización durable recomendada;
- una sola siguiente acción.
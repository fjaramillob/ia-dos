# Execution Task

Consulta [Registro de tipos de ejecución](../docs/execution/execution-task-types.md).

## Identificación

- ID: `[TASK-ID]`
- Título: `[TÍTULO BREVE]`
- Fuente canónica: `[ISSUE, ARCHIVO O URL]`
- Estado: `Propuesta | Aprobada | En ejecución | Bloqueada | Completada | Cancelada`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Conversation Space de origen: `[NOMBRE]`
- Tipo de ejecución principal: `[INSPECT | BOOTSTRAP | BUILD | FIX | REFACTOR | MIGRATE | TEST | HARDEN | DOCUMENT | WIKI | RELEASE | OPERATE]`
- Tipo secundario, solo si es inseparable: `[TIPO O NINGUNO]`
- Responsable humano: `[ROL O PERSONA]`
- Coding agent: `[HERRAMIENTA O AGENTE DISPONIBLE]`
- Espacio de retorno: `[TÓPICO Y NOMBRE DEL ESPACIO QUE REVISARÁ EL REPORTE]`

El tipo clasifica el modo de trabajo, pero no concede permisos.

## Objetivo

Describe un único resultado concreto y verificable.

## Contexto mínimo

- Fuentes obligatorias: `[RUTAS O URL]`
- `CORE`, si aporta: `[RUTA, URL O NO REQUERIDO]`
- Context Pack principal, si aporta: `[RUTA, URL O NO REQUERIDO]`
- Archivos o rutas relevantes:
  - `[RUTA]`

No copies toda la historia del proyecto.

## Problema o evidencia inicial

Describe qué ocurre hoy y qué evidencia lo confirma. Para `INSPECT`, indica qué debe determinarse. Para `FIX`, incluye reproducción. Para `MIGRATE`, identifica fuente y destino.

## Alcance

### Incluido

- `[CAMBIO O ANÁLISIS AUTORIZADO]`

### Fuera de alcance

- `[CAMBIO NO AUTORIZADO]`

## Repositorios y zonas autorizadas

- Repositorio: `[APP, WIKI U OTRO]`
- Rama o modo de trabajo: `[RAMA / SOLO LECTURA / MODIFICACIÓN LOCAL]`
- Rutas permitidas:
  - `[RUTA]`
- Rutas prohibidas:
  - `[RUTA]`

## Capacidades y autorizaciones

- Lectura: `Autorizada | No autorizada`
- Escritura local: `Autorizada | No autorizada`
- Crear branch: `Autorizado | No autorizado`
- Commit: `Autorizado | No autorizado`
- Push: `Autorizado | No autorizado`
- Pull request: `Autorizado | No autorizado`
- Merge: `Autorizado | No autorizado`
- Despliegue o producción: `Autorizado | No autorizado`
- Recursos externos, datos o costes: `[AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]`

## Guardrails

- no ampliar alcance sin aprobación;
- no usar referencias de otros proyectos;
- no modificar secretos ni recursos externos sin autorización;
- no cambiar arquitectura, dependencias o seguridad salvo alcance explícito;
- preservar comportamiento no relacionado;
- detenerse ante contradicciones con fuentes o estado real;
- no afirmar verificación sin evidencia.

Agrega guardrails propios del proyecto y del tipo de ejecución.

## Criterios de aceptación

- [ ] `[RESULTADO OBSERVABLE]`
- [ ] `[RESULTADO OBSERVABLE]`

## Pruebas y verificaciones

- `[COMANDO, REVISIÓN O PROCEDIMIENTO]`

Declara evidencia esperada: salida de pruebas, diff, captura, enlace a CI, matriz, árbol o verificación manual.

## Condiciones de detención

Detente y reporta sin improvisar cuando:

- falte información crítica;
- el working tree tenga cambios no identificados;
- se requiera tocar rutas o recursos no autorizados;
- una verificación crítica falle;
- aparezca un riesgo de seguridad, pérdida de datos o coste;
- sea necesaria una decisión de producto, arquitectura u operación no confirmada;
- el tipo de ejecución declarado ya no represente el trabajo real.

## Documentación y memoria

- Archivos técnicos a actualizar: `[RUTAS O NINGUNO]`
- Información durable que debe volver a la Wiki: `[RUTAS, DECISIONES O NINGUNA]`
- ADR requerido: `Sí | No`

## Entrega requerida

El agente debe devolver un reporte usando `execution-report.template.md`, incluyendo:

- tópico y espacio de retorno;
- tipo de ejecución realmente realizado;
- resultado observable;
- archivos o fuentes revisadas;
- pruebas y evidencia;
- autorizaciones utilizadas;
- fuera de alcance respetado;
- desviaciones, riesgos y decisiones pendientes;
- actualización durable recomendada.
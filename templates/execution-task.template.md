# Execution Task

## Identificación

- ID: `[TASK-ID]`
- Título: `[TÍTULO BREVE]`
- Fuente canónica: `[ISSUE, ARCHIVO O URL]`
- Estado: `Propuesta | Aprobada | En ejecución | Bloqueada | Completada | Cancelada`
- Responsable humano: `[ROL O PERSONA]`
- Coding agent: `[HERRAMIENTA O AGENTE]`

## Objetivo

Describe el resultado concreto que debe existir al finalizar.

## Contexto mínimo

- `CORE`: `[RUTA O URL]`
- Context Pack principal: `[RUTA O URL]`
- Context Pack secundario, solo si es necesario: `[RUTA O URL]`
- Archivos o rutas relevantes:
  - `[RUTA]`

No copies aquí toda la historia del proyecto.

## Problema o evidencia

Describe qué ocurre hoy y qué evidencia confirma el problema.

## Alcance

### Incluido

- `[CAMBIO AUTORIZADO]`

### Fuera de alcance

- `[CAMBIO NO AUTORIZADO]`

## Repositorios y zonas autorizadas

- Repositorio: `[APP, WIKI U OTRO]`
- Rama de trabajo: `[RAMA]`
- Rutas permitidas:
  - `[RUTA]`
- Rutas prohibidas:
  - `[RUTA]`

## Guardrails

- no ampliar alcance sin aprobación;
- no modificar secretos, producción ni recursos externos;
- no cambiar dependencias, arquitectura o seguridad salvo autorización explícita;
- preservar compatibilidad y comportamiento no relacionado;
- detenerse ante contradicciones con la wiki o el estado real;
- no afirmar verificación sin evidencia.

Agrega aquí guardrails específicos del proyecto.

## Criterios de aceptación

- [ ] `[RESULTADO OBSERVABLE]`
- [ ] `[RESULTADO OBSERVABLE]`

Cada criterio debe poder comprobarse.

## Pruebas y verificaciones

- `[COMANDO, REVISIÓN O PROCEDIMIENTO]`

Indica qué evidencia debe conservarse: salida de pruebas, captura, diff, enlace a CI o verificación manual.

## Condiciones de detención

Detente y reporta sin improvisar cuando:

- falte información crítica;
- el working tree contenga cambios no identificados;
- se requiera tocar rutas fuera del alcance;
- una prueba crítica falle;
- aparezca un riesgo de seguridad, pérdida de datos o coste;
- sea necesaria una decisión de producto o arquitectura no confirmada.

## Documentación y memoria

- Archivos técnicos a actualizar: `[RUTAS O NINGUNO]`
- Información que debe volver a la wiki: `[RUTAS O DECISIONES]`
- ADR requerido: `Sí | No`

## Entrega requerida

El agente debe devolver un reporte usando `execution-report.template.md`, incluyendo:

- resumen del resultado;
- archivos modificados;
- pruebas y evidencia;
- fuera de alcance respetado;
- riesgos y limitaciones;
- decisiones pendientes;
- actualización recomendada para la wiki.

# Wiki Update Task

## Identificación

- ID: `[TASK-ID]`
- Título: `[TÍTULO BREVE]`
- Estado: `Propuesta | Aprobada | En ejecución | Bloqueada | Completada | Cancelada`
- Responsable humano: `[ROL O PERSONA]`
- Project Orchestrator: `[PLATAFORMA O ASISTENTE]`
- Coding agent: `[CODEX, ANTIGRAVITY, CLAUDE CODE U OTRO]`

## Objetivo documental

Describe el conocimiento durable que debe quedar creado, actualizado, corregido o retirado.

## Fuente del conocimiento

- Conversación o handoff: `[REFERENCIA]`
- Evidencia del repositorio: `[RUTAS]`
- Pull request o Execution Report: `[REFERENCIA]`
- Documento o fuente externa: `[REFERENCIA]`

No trates una conversación o fuente sin revisar como decisión durable.

## Clasificación del contenido

- Hechos verificados:
  - `[HECHO]`
- Decisiones confirmadas:
  - `[DECISIÓN]`
- Hipótesis o propuestas:
  - `[HIPÓTESIS]`
- Preguntas abiertas:
  - `[PREGUNTA]`
- Contradicciones conocidas:
  - `[CONTRADICCIÓN]`

## Contexto mínimo

- `CORE`: `[RUTA]`
- Páginas que deben leerse:
  - `[RUTA]`
- Archivos de aplicación o evidencia relevante:
  - `[RUTA]`

## Repositorio y zonas autorizadas

- Repositorio de la wiki: `[REPOSITORIO]`
- Branch de trabajo: `[BRANCH]`
- Páginas autorizadas:
  - `[RUTA]`
- Rutas prohibidas:
  - `[RUTA]`
- Contenido que debe preservarse:
  - `[DESCRIPCIÓN O RUTA]`

## Alcance

### Incluido

- `[CAMBIO DOCUMENTAL AUTORIZADO]`

### Fuera de alcance

- `[CAMBIO NO AUTORIZADO]`

## Guardrails

- no inventar información;
- no convertir hipótesis o propuestas en hechos;
- no presentar como implementado algo sin evidencia;
- no duplicar fuentes de verdad sin necesidad;
- no eliminar contenido vigente sin justificación;
- no guardar secretos ni datos no permitidos;
- no modificar rutas fuera del alcance;
- detenerse ante contradicciones no resueltas.

## Criterios de aceptación

- [ ] Las páginas autorizadas reflejan el conocimiento confirmado.
- [ ] Hechos, decisiones, hipótesis y preguntas abiertas están diferenciados.
- [ ] El estado real no se confunde con planes futuros.
- [ ] La navegación y los enlaces fueron actualizados cuando corresponde.
- [ ] No se modificaron rutas fuera del alcance.
- [ ] El diff es revisable y no contiene secretos.

Agrega criterios específicos y observables para la tarea.

## Validaciones requeridas

- `[VALIDACIÓN DE MARKDOWN]`
- `[VALIDACIÓN DE YAML]`
- `[REVISIÓN DE ENLACES]`
- `[REVISIÓN MANUAL REPRODUCIBLE]`
- revisión completa del diff;
- confirmación de archivos creados, modificados o eliminados.

## Condiciones de detención

Detente y reporta cuando:

- falte una decisión necesaria;
- exista una contradicción que cambie el contenido final;
- la wiki real no coincida con el contexto entregado;
- se requiera tocar rutas no autorizadas;
- aparezcan cambios ajenos en el working tree;
- una validación crítica falle;
- se detecten secretos o información sensible.

## Git y pull request

- Crear branch dedicada: `Sí | No`
- Crear commits: `Sí | No`
- Abrir pull request: `Sí | No`
- Fusionar: `Solo con autorización explícita`

## Entrega requerida

Devuelve un `Execution Report` que incluya:

- resumen del conocimiento materializado;
- archivos creados, modificados o eliminados;
- fuentes utilizadas;
- validaciones ejecutadas y resultados;
- contradicciones o pendientes;
- fuera de alcance respetado;
- referencia al pull request;
- recomendación de revisión para el Project Orchestrator.

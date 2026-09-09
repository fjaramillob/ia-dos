# Execution Task

Consulta:

- `docs/execution/execution-task-types.md`;
- `docs/execution/source-and-artifact-authority.md`;
- `docs/orchestration/context-compression-by-authority.md`;
- `docs/orchestration/typed-artifact-routing.md`.

## Encabezado obligatorio

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar outcome o frontera | aprobar el propio resultado | iniciar otra unidad
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID]
```

El transporte no cambia este contrato. `Authority Envelope` y `<TASK-ID>-CHECKPOINT.md` no son Artifact Types.

## Precondiciones de emisión

Antes de emitir la tarea confirma:

- [ ] el outcome está definido, es cohesivo, acotado y verificable bajo una frontera estable de autoridad;
- [ ] Memory Bootstrap Gate = `PASS | BOOTSTRAP REQUIRED — ESTA TAREA MATERIALIZA EL CHECKPOINT DURABLE | NO APLICA`;
- [ ] readiness indispensable = `LISTO PARA EJECUCIÓN | NO APLICA`;
- [ ] Planning previo = `[REFERENCIA REVISADA | NO APLICA]`;
- [ ] las decisiones humanas indispensables para esta frontera están resueltas;
- [ ] la Task puede llegar a Final State sin cambiar materialmente outcome, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno.

No dividas una Task sólo por duración, cantidad de archivos/comandos o porque incluya implementación, tests, commit, push, deploy o smoke.

## Identificación

- Cycle ID: `[CYCLE-ID O NO APLICA]`
- Task ID: `[TASK-ID]`
- Título: `[TÍTULO BREVE]`
- Estado: `Propuesta | Autorizada | En ejecución | Bloqueada | Completada | Cancelada`
- Tópico de origen: `[00 | 10 | 20 | 30 | 40 | 50 | 90]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino del Execution Report: `[CONVERSATION SPACE]`
- Tipo principal: `[INSPECT | BOOTSTRAP | BUILD | FIX | REFACTOR | MIGRATE | TEST | HARDEN | DOCUMENT | WIKI | RELEASE | OPERATE]`
- Execution Cell o sesión: `[NOMBRE O NO APLICA]`
- Implementation Plan revisado: `[REFERENCIA O NO APLICA]`
- Environment Readiness Report: `[REFERENCIA LISTO PARA EJECUCIÓN O NO APLICA]`

El Conversation Agent asigna el Task ID al construir la Task real. Una candidata de Planning mantiene `Task ID: PENDIENTE — ASIGNAR AL ADOPTAR`.

## Outcome

Describe un único resultado definido, cohesivo, terminable y verificable.

Un outcome puede requerir múltiples fases internas siempre que compartan la misma frontera de autoridad.

## Fuentes de autoridad

| Recurso | Rol | Autoridad para | Acceso permitido | Limitaciones |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[LÍMITES]` |

Incluye instrucciones locales aplicables, por ejemplo `AGENTS.md`.

## Delta del ciclo

- `[DECISIÓN O CAMBIO QUE HABILITA ESTA EJECUCIÓN]`
- `[EVIDENCIA ACTUAL]`
- `[BLOQUEO RESUELTO]`
- `[TRABAJO QUE DEBE PRESERVARSE]`

No vuelvas a narrar el proyecto.

## Embedded Contract

Debe viajar dentro de esta Task:

- outcome;
- alcance y fuera de alcance;
- Authority Envelope;
- seguridad y datos;
- criterios de aceptación;
- verificaciones;
- condiciones de detención;
- Output Delivery cuando corresponda.

## Required Reading

- `[DOCUMENTO CONCRETO O NINGUNO]`

El Coding Agent debe leer estos documentos antes de actuar.

## References

- `[RUTA, COMMIT, PR, WIKI, REPORTE O NINGUNA]`

Aportan trazabilidad o navegación; no implican lectura por defecto.

Una Task es suficientemente autocontenida cuando `Task + Required Reading` permite ejecutarla correctamente sin conversaciones previas.

## Readiness del entorno

- Entorno: `[LOCAL / REMOTO / COMBINADO / OTRO]`
- Estado: `LISTO PARA EJECUCIÓN | NO APLICA`
- Evidencia o reporte: `[REFERENCIA]`
- Estado que debe preservarse: `[DETALLE]`
- Accesos o secretos no disponibles: `[NINGUNO O DETALLE NO SENSIBLE]`

No inventes rutas, credenciales, herramientas o permisos.

## Alcance

### Incluido

- `[CAMBIO O ACCIÓN AUTORIZADA]`

### Fuera de alcance

- `[CAMBIO O ACCIÓN NO AUTORIZADA]`

## Zonas autorizadas

- recursos o artefactos modificables: `[LISTA]`
- rama o modo de trabajo: `[RAMA / SOLO LECTURA / MODIFICACIÓN LOCAL / OTRO]`
- rutas o áreas permitidas: `[LISTA]`
- rutas o áreas prohibidas: `[LISTA]`

## Authority Envelope

Declara explícitamente todas las capacidades que el outcome puede utilizar.

```text
Code:
- [LECTURA / ESCRITURA / ACCIONES]

Git:
- branch: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- stage selectivo: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- commit: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- push: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- pull request: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- merge: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- force push: [AUTORIZADO / NO AUTORIZADO]

Delivery:
- [DEPLOY / RELEASE / NINGUNO]

Production:
- [SMOKE / OPERACIÓN / NINGUNO]

Data / External / Cost:
- [AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]

No autorizado:
- [LÍMITES EXPLÍCITOS]
```

Regla:

```text
acción sensible no declarada
→ no autorizada

acción declarada + gates cumplidos + frontera estable
→ no requiere otra ida y vuelta humana por rutina

cambio material de frontera
→ STOP
```

El coding agent nunca aprueba su propio plan o ejecución.

## Fases internas permitidas

Declara sólo si ayuda a la ejecución. Ejemplo:

```text
Revalidate
→ Implement
→ Verify
→ Commit
→ Push
→ Deploy
→ Production Smoke
→ Final State
```

Estas fases no son Tasks separadas por defecto.

## Execution Checkpoint opcional

Cuando una tarea larga o un cambio de Coding Agent lo justifique, puede materializarse:

```text
<TASK-ID>-CHECKPOINT.md
```

Contenido recomendado:

- fase alcanzada;
- HEAD o referencia técnica equivalente;
- worktree;
- fases completadas;
- pendiente;
- bloqueos;
- observaciones necesarias para continuar.

`Checkpoint ≠ autorización`. No amplía el Authority Envelope y no sustituye Execution Resume.

## Output Delivery

```text
Output Delivery:
Channel: [Exchange | Conversation | Otro]
Location: [outbox | destino lógico | NO APLICA]
Filename: [{TASK-ID}-REPORT.md | OTRO | NO APLICA]
Caveman Return: [Sí | No]
```

Si usa Exchange, ese permiso cubre únicamente el output declarado. Exchange permanece pasivo y provider-agnostic.

## Criterios de aceptación

- [ ] `[RESULTADO OBSERVABLE]`

## Verificaciones

- `[COMANDO, REVISIÓN O PROCEDIMIENTO]`
- evidencia esperada: `[SALIDA O PRUEBA]`

## Condiciones de detención

Detente y reporta cuando:

- falte información crítica;
- exista trabajo previo no identificado que pueda perderse;
- aparezca una instrucción local aplicable incompatible;
- sea necesario tocar recursos o usar capacidades no autorizadas;
- falle una verificación crítica;
- aparezca riesgo de seguridad, pérdida de datos o coste no cubierto;
- sea necesaria una decisión no confirmada;
- cambie materialmente outcome, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno;
- una precondición de memoria o readiness deje de cumplirse.

## Contrato de retorno

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión de evidencia bajo la autoridad aplicable
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El Report debe ser evidence-first y proporcional. Estructura preferente:

```text
Outcome
Evidence
Actual Scope
Acceptance
Deviations
Final State
```

Agrega otras secciones sólo cuando aporten evidencia real. No vuelvas a narrar la Task.

Si `Caveman Return: Sí` y el Report completo fue materializado correctamente, responde en conversación únicamente:

```text
EJECUCIÓN: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN O NINGUNA]
Reporte: [NOMBRE/PATH]
```

No repitas tests, commits, deploy, smoke ni detalle que ya vive en el Report.

## Autoridad posterior

El Cycle Owner revisa dentro de autoridad delegada. La persona responsable interviene cuando la decisión posterior cambia materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.
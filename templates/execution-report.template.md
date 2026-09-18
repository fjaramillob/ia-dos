# Execution Report

El `Execution Report` registra **qué ocurrió realmente** durante una Execution Task. No vuelve a narrar qué estaba autorizado, no decide por el Cycle Owner ni sustituye la aprobación humana aplicable. Cuando la Task incluye contrato de memoria, reporta qué se materializó sin convertir evidencia en dirección del proyecto.

```text
Task
→ qué estaba autorizado

Report
→ qué ocurrió realmente
```

## Encabezado

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión de evidencia bajo la autoridad aplicable
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

`Estado` describe únicamente el resultado de la ejecución.

`Atención requerida` identifica un bloqueo, riesgo, desviación o decisión concreta que requiere revisión. No selecciona `APROBAR`, `CORREGIR`, `REVERTIR`, `ESCALAR` o `REVISAR MEMORIA`.

## Outcome

Describe brevemente el resultado observable alcanzado.

No copies el objetivo completo de la Task salvo que sea necesario para explicar una desviación.

## Evidence

Incluye sólo la evidencia necesaria para verificar el outcome, por ejemplo:

- tests, lint, typecheck o build realmente ejecutados;
- diff o revisión de archivos relevante;
- commit/PR/deployment sólo si ocurrieron;
- smoke o verificación funcional realmente realizada;
- comandos, logs, URLs o identificadores cuando aporten trazabilidad.

No declares evidencia que no existe.

## Actual Scope

Resume qué recursos o áreas fueron realmente modificados o inspeccionados.

```text
Modificado:
- [RECURSO / CAMBIO]

Sólo inspeccionado:
- [RECURSO O NINGUNO]
```

Incluye metadata técnica sólo cuando sea relevante para comprobar la tarea.

## Acceptance

| Criterio | Resultado | Evidencia |
|---|---|---|
| `[CRITERIO]` | `PASS | FAIL | NO VERIFICADO` | `[EVIDENCIA]` |

No repitas criterios que no pertenecían a la Task.

## Deviations

- `Ninguna`, o
- `[DIFERENCIA ENTRE LO AUTORIZADO Y LO REALMENTE EJECUTADO, MOTIVO Y EFECTO]`

Una ampliación de alcance ocurrida no queda legitimada por aparecer aquí.

Si se activó una condición de detención, indícala aquí o en `Atención requerida` según corresponda.

## Final State

Registra sólo el estado final necesario para continuar o cerrar con seguridad, por ejemplo:

- HEAD o versión final cuando exista;
- branch/worktree cuando sea relevante;
- estado de deployment/producción cuando haya sido parte del Authority Envelope;
- artifacts de output materializados;
- bloqueo restante del alcance original;
- `Ninguno` cuando no exista estado adicional relevante.

## Durable Memory Impact

Declara siempre que la Task incluya Memory Policy:

```text
Durable Memory Impact:
NONE | UPDATED | DEFERRED | ATTENTION REQUIRED
```

- `NONE`: no hubo cambio semántico durable;
- `UPDATED`: la memoria autorizada quedó actualizada;
- `DEFERRED`: el outcome individual no justificó consolidación semántica todavía;
- `ATTENTION REQUIRED`: existe una decisión, contradicción o cambio material que requiere gobierno.

Explica brevemente las rutas afectadas cuando sea `UPDATED`. No inventes una recomendación de roadmap.

## Operational Baseline

Declara cuando el proyecto tenga estado publicado o la Task lo exija:

```text
Operational Baseline:
UNCHANGED | UPDATED | NO APLICA | BLOQUEADO
```

Si fue `UPDATED`, registra la evidencia necesaria para continuar con seguridad: repositorio/branch, último HEAD remoto verificado, commit o versión publicada, deployment/release, entorno/URL, estado y fecha de verificación, según aplique.

Si `Repository HEAD != Production Commit`, conserva ambos valores.

Si una nueva publicación requería baseline durable y no pudo actualizarse, usa `BLOQUEADO` o explica la limitación; no ocultes la brecha bajo `COMPLETADO`.

## Secciones opcionales

Agrega otras secciones únicamente cuando aporten evidencia real a esta ejecución. Ejemplos:

- seguridad o datos, si la Task los tocó;
- rollback/recovery, si fue necesario;
- costos o recursos externos, si fueron utilizados;
- compatibilidad/migración, si fue criterio del outcome.

No uses el Report como checklist ceremonial de permisos que no se utilizaron.

## Frontera con memoria durable

Los hechos descubiertos pueden aparecer como evidencia del outcome. El Report no convierte hallazgos en memoria semántica por iniciativa propia.

Cuando la Task declara `Memory Policy`, el Report registra el resultado de esa política. La decisión sobre triggers y dirección sigue perteneciendo al Cycle Owner/persona responsable.

Una Task separada de Wiki se usa sólo cuando bootstrap, consolidación, reparación o una frontera de autoridad distinta lo justifican.

## Caveman Return

Cuando la Task declara:

```text
Output Delivery:
Channel: Exchange
Location: outbox
Filename: <TASK-ID>-REPORT.md
Caveman Return: Sí
```

y este Report completo fue materializado correctamente, la respuesta conversacional debe reducirse a:

```text
EJECUCIÓN: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN O NINGUNA]
Reporte: [NOMBRE/PATH]
```

No repitas en chat tests, paths, commits, deploy, smoke ni otro detalle que ya viva aquí.

## Declaración final

Antes de devolver el Report confirma:

- [ ] el estado refleja lo realmente ocurrido;
- [ ] la evidencia reportada fue realmente obtenida;
- [ ] Actual Scope coincide con las acciones realizadas;
- [ ] las desviaciones no fueron ocultadas;
- [ ] no se afirma aprobación del propio resultado;
- [ ] no se inicia otra unidad;
- [ ] Durable Memory Impact coincide con lo realmente materializado cuando aplica;
- [ ] Operational Baseline refleja la publicación real cuando aplica;
- [ ] no se inventa dirección o prioridad a partir de la memoria;
- [ ] el Report vuelve al destino declarado.
# Execution Report

El `Execution Report` registra **qué ocurrió realmente** durante una Execution Task. No vuelve a narrar qué estaba autorizado, no decide por el Cycle Owner, no sustituye la aprobación humana aplicable y no consolida memoria durable por defecto.

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

## Secciones opcionales

Agrega otras secciones únicamente cuando aporten evidencia real a esta ejecución. Ejemplos:

- seguridad o datos, si la Task los tocó;
- rollback/recovery, si fue necesario;
- costos o recursos externos, si fueron utilizados;
- compatibilidad/migración, si fue criterio del outcome.

No uses el Report como checklist ceremonial de permisos que no se utilizaron.

## Frontera con memoria durable

Los hechos descubiertos pueden aparecer como evidencia del outcome. El Report no crea por defecto una sección de “conocimiento durable” ni recomienda automáticamente qué incorporar a una LLM Wiki.

La evaluación de memoria ocurre después de revisar evidencia, salvo actualización documental concreta ya autorizada dentro de la Task.

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
- [ ] no se recomienda memoria durable por rutina;
- [ ] el Report vuelve al destino declarado.
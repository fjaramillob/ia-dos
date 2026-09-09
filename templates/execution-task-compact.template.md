# Execution Task compacta

Usa este bloque por defecto cuando el outcome está definido, es cohesivo y verificable bajo una frontera estable de autoridad, la precondición de memoria permite la unidad, el entorno está listo cuando corresponde y existe autoridad aplicable.

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar outcome o frontera | autoaprobación | siguiente unidad

Método: IA-DOS
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [EXEC-ID]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Destino: [CONVERSATION SPACE]
Tipo: [INSPECT | BOOTSTRAP | BUILD | FIX | REFACTOR | MIGRATE | TEST | HARDEN | DOCUMENT | WIKI | RELEASE | OPERATE]

OUTCOME
[RESULTADO DEFINIDO, COHESIVO, ACOTADO Y VERIFICABLE]

PRECONDICIONES
- Memory Bootstrap Gate: [PASS | BOOTSTRAP REQUIRED — ESTA TAREA MATERIALIZA EL CHECKPOINT DURABLE | NO APLICA]
- Readiness indispensable: [LISTO PARA EJECUCIÓN | NO APLICA]
- Planning previo: [REFERENCIA REVISADA | NO APLICA]
- autorización humana adicional requerida: [RESUELTA | NO APLICA]

FUENTES DE AUTORIDAD
| Recurso o documento | Rol | Autoridad para | Acceso | Vigencia o referencia |
|---|---|---|---|---|
| [RECURSO] | [ROL] | [ÁMBITO] | [LECTURA / ESCRITURA / ACCIÓN] | [RUTA, VERSIÓN, COMMIT O FECHA] |

DELTA DEL CICLO
- [DECISIÓN O CAMBIO QUE HABILITA ESTA EJECUCIÓN]
- [EVIDENCIA ACTUAL]
- [BLOQUEO RESUELTO]
- [TRABAJO QUE DEBE PRESERVARSE]

EMBEDDED CONTRACT
Incluido:
- [CAMBIO AUTORIZADO]

Fuera de alcance:
- [CAMBIO NO AUTORIZADO]

Zonas:
- modificables: [RECURSOS O RUTAS]
- prohibidas: [RECURSOS O RUTAS]
- rama o modo: [RAMA / MODIFICACIÓN LOCAL / OTRO]

REQUIRED READING
- [DOCUMENTO CONCRETO O NINGUNO]

REFERENCES
- [TRAZABILIDAD/NAVEGACIÓN O NINGUNA]

Task + Required Reading deben bastar para ejecutar sin depender de conversaciones previas.

AUTHORITY ENVELOPE
Code:
- lectura: [AUTORIZADA / NO AUTORIZADA]
- escritura: [AUTORIZADA / NO AUTORIZADA]

Git:
- branch: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- stage selectivo: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- commit: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- push: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- pull request: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- merge: [AUTORIZADO / NO AUTORIZADO / NO APLICA]
- force push: [AUTORIZADO / NO AUTORIZADO]

Delivery:
- [AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]

Production:
- [AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]

Data / External / Cost:
- [AUTORIZACIÓN EXPLÍCITA O NO AUTORIZADO]

No autorizado:
- [LÍMITES]

Regla: acción sensible no declarada → no autorizada. Acción declarada + gates cumplidos + frontera estable → puede ejecutarse dentro de esta Task sin otra ida y vuelta humana por rutina.

FASES INTERNAS, SI APORTA
[Revalidate → Implement → Verify → Commit → Push → Deploy → Production Smoke → Final State]

No dividas sólo por duración, archivos, comandos o fases internas. Detente si cambia materialmente outcome, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno.

EXECUTION CHECKPOINT OPCIONAL
- archivo: [<EXEC-ID>-CHECKPOINT.md | NO APLICA]
- uso: continuidad operacional o cambio de Coding Agent
- autoridad: ninguna; la Task sigue gobernando

OUTPUT DELIVERY
- Channel: [Exchange | Conversation | Otro]
- Location: [outbox | destino lógico | NO APLICA]
- Filename: [{EXEC-ID}-REPORT.md | OTRO | NO APLICA]
- Caveman Return: [Sí | No]

CRITERIOS DE ACEPTACIÓN
- [ ] [RESULTADO OBSERVABLE]

VERIFICACIONES
- [COMANDO, REVISIÓN O PROCEDIMIENTO]
- evidencia esperada: [SALIDA O PRUEBA]

CONDICIONES DE DETENCIÓN
Detente ante información crítica faltante, trabajo previo en riesgo, instrucciones incompatibles, capacidad no autorizada, verificación crítica fallida, riesgo de seguridad/datos/coste no cubierto o cualquier cambio material de la frontera declarada.

CONTRATO DE RETORNO
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Execution Task ID: [EXEC-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]

Reporta proporcionalmente:
Outcome
Evidence
Actual Scope
Acceptance
Deviations
Final State

No vuelvas a narrar la Task.

Si `Caveman Return: Sí` y el Report completo fue materializado correctamente, responde únicamente:

EJECUCIÓN: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN O NINGUNA]
Reporte: [NOMBRE/PATH]
```

## Reglas

- `Authority Envelope`, `Execution Checkpoint`, `Output Delivery` y `Caveman Return` no son Artifact Types.
- Cada Task vuelve a declarar permisos aunque reutilice la misma Execution Cell.
- Un Checkpoint registra continuidad, no autoridad.
- Exchange, cuando se adopta, sigue siendo opcional, pasivo y provider-agnostic.
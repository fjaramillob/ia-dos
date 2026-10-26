# Execution Resume

Usa este artefacto para reanudar la **misma Execution Task** después de una interrupción real, una acción externa o un bloqueo que el executor no podía resolver dentro de su autoridad.

No lo uses para debugging ordinario, repair-in-place o safe retry mientras la misma Execution siga abierta bajo `Adaptation Authority: BOUNDED`.

Sólo aplica si permanecen sin cambios:

- outcome;
- Protected Invariants;
- Protected Boundaries;
- alcance;
- Authority Envelope;
- seguridad;
- arquitectura.

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: nueva Planning Task | replantear arquitectura | ampliar alcance | ampliar permisos | cambiar Protected Invariants | cruzar una Protected Boundary nueva
Cycle ID: [MISMO CYCLE-ID O NO APLICA]
Task ID: [MISMO EXECUTION TASK ID]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Destino: [CONVERSATION SPACE]

CONDICIÓN EXTERNA O INTERRUPCIÓN QUE BLOQUEÓ
[CONDICIÓN]

EVIDENCIA DE RESOLUCIÓN
[COMANDO, SALIDA O CONFIRMACIÓN]

VERIFICACIÓN PREVIA OBLIGATORIA
[COMPROBACIÓN NO DESTRUCTIVA]

PUNTO DE REANUDACIÓN
[ETAPA EXACTA]

FRONTERAS QUE DEBEN SEGUIR VIGENTES
- outcome: sin cambios
- Protected Invariants: sin cambios
- Protected Boundaries: sin cambios
- alcance: sin cambios
- Authority Envelope: sin cambios
- arquitectura: sin cambios
- seguridad: sin cambios

AUTORIZACIONES VIGENTES
[REFERENCIA A LA EXECUTION TASK APROBADA]

CAMBIOS EXTERNOS AL CODING AGENT
[CAMBIO REALIZADO POR LA PERSONA/ACTOR EXTERNO, O NINGUNO]

No replanifiques por rutina. No abras otro ciclo. No amplíes permisos.

Detente si la verificación previa falla, si aparece estado parcial/irreversible no cubierto por recovery, o si el estado real invalida cualquiera de las fronteras anteriores. En ese caso devuelve evidencia al Cycle Owner: corresponde una nueva decisión, Execution Task o Planning sólo si existe una decisión material pendiente.
```

Semántica:

```text
Execution Resume
= Task original
+ delta del bloqueo externo o interrupción real resuelta
```

Si la tarea original utiliza una Execution Cell activa y sigue respondiendo bien, reanuda en esa misma célula. No crees una conversación nueva sólo por el bloqueo resuelto.

# Execution Resume

Usa este artefacto cuando una condición bloqueante se resolvió sin cambiar objetivo, alcance, autoridad, arquitectura o seguridad de la Execution Task aprobada.

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: nueva Planning Task | replantear arquitectura | ampliar alcance | ampliar permisos
Cycle ID: [MISMO CYCLE-ID O NO APLICA]
Task ID: [MISMO EXECUTION TASK ID]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Destino: [CONVERSATION SPACE]

CONDICIÓN QUE BLOQUEÓ
[CONDICIÓN]

EVIDENCIA DE RESOLUCIÓN
[COMANDO, SALIDA O CONFIRMACIÓN]

VERIFICACIÓN PREVIA OBLIGATORIA
[COMPROBACIÓN NO DESTRUCTIVA]

PUNTO DE REANUDACIÓN
[ETAPA EXACTA]

FRONTERAS QUE DEBEN SEGUIR VIGENTES
- objetivo: sin cambios
- alcance: sin cambios
- autoridad: sin cambios
- arquitectura: sin cambios
- seguridad: sin cambios

AUTORIZACIONES VIGENTES
[REFERENCIA A LA EXECUTION TASK APROBADA]

CAMBIOS EXTERNOS AL CODING AGENT
[CAMBIO REALIZADO POR LA PERSONA, O NINGUNO]

No replanifiques. No abras otro ciclo. No amplíes permisos.

Detente si la verificación previa falla o si el estado real invalida alguna de las fronteras anteriores. En ese caso, devuelve evidencia al Cycle Owner: corresponde una nueva Execution Task o Planning, no un Resume.
```

Si la tarea original utiliza una Execution Cell activa y sigue respondiendo bien, reanuda en esa misma célula. No crees una conversación nueva sólo por el bloqueo resuelto.

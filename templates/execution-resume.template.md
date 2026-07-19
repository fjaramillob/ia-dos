# Execution Resume

Usa este artefacto cuando una condición bloqueante se resolvió sin cambiar objetivo, alcance, arquitectura o seguridad de la Execution Task aprobada.

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: nueva Planning Task | replantear arquitectura | ampliar alcance
Cycle ID: [MISMO CYCLE-ID]
Task ID: [MISMO EXECUTION TASK ID]
Agent Session: [SESIÓN ORIGINAL O RESUME — RESULTADO]
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

AUTORIZACIONES VIGENTES
[REFERENCIA A LA EXECUTION TASK APROBADA]

CAMBIOS EXTERNOS AL CODING AGENT
[CAMBIO REALIZADO POR EL USUARIO O NINGUNO]

No replanifiques. No abras otro ciclo. Detente si la verificación previa falla o si el estado real vuelve inválida la tarea aprobada.
```

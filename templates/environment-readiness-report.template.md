# Environment Readiness Report

Usa este retorno después de ejecutar un `Environment Preflight` de solo lectura.

```text
Artifact Type: Environment Readiness Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: Autorizar ejecución | Resolver dependencia | Corregir preflight | Escalar
Forbidden Output: iniciar ejecución automáticamente | modificar el entorno
Cycle ID: [CYCLE-ID]
Task ID: [PREFLIGHT-ID]
Agent Session: PREFLIGHT — [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]

Estado: LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
Dependencia dominante: [ELEMENTO O NINGUNA]
Evidencia:
- [COMANDO, SALIDA O REFERENCIA]
Acción mínima requerida: [ACCIÓN O NINGUNA]
Cambios realizados: Ninguno

No autorices ejecución cuando el estado sea NO LISTO o DESCONOCIDO.
```

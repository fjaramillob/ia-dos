# Environment Readiness Report

Usa este retorno después de ejecutar un `Environment Preflight` de solo lectura sobre el entorno.

```text
Artifact Type: Environment Readiness Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión del readiness y decisión bajo la autoridad aplicable
Forbidden Output: iniciar ejecución automáticamente | modificar el entorno
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [PREFLIGHT-ID]
Sesión de planificación, cuando aporte: [PREFLIGHT — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]

Estado: LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
Dependencia dominante: [ELEMENTO O NINGUNA]
Evidencia:
- [COMANDO, SALIDA O REFERENCIA]
Acción mínima requerida: [ACCIÓN O NINGUNA]
Cambios al entorno: Ninguno
Materialización del propio reporte: [RUTA/NOMBRE AUTORIZADO | Conversación | NO APLICA]
```

`Estado` describe exclusivamente readiness del entorno.

- `LISTO PARA EJECUCIÓN`: las precondiciones indispensables comprobadas permiten considerar autorización de escritura;
- `NO LISTO`: existe una dependencia concreta sin resolver;
- `DESCONOCIDO`: la evidencia disponible no permite confirmar readiness.

No autorices ni reanudes escritura cuando el estado sea `NO LISTO` o `DESCONOCIDO`.

El coding agent no resuelve la dependencia automáticamente salvo una tarea posterior que lo autorice. El Cycle Owner revisa dentro de la autoridad delegada y la persona responsable interviene cuando la acción requerida necesita aprobación humana.

La materialización explícitamente autorizada de este propio reporte no cuenta como modificación del entorno inspeccionado y no concede permisos adicionales.

El campo de sesión de planificación es opcional y no obliga a abrir una conversación nueva.

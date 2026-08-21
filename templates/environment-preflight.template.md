# Environment Preflight

Usa este artefacto cuando una futura Execution Task dependa de una precondición indispensable del entorno que todavía no está comprobada.

```text
Artifact Type: Environment Preflight
Destination Role: Coding Agent — Planning
Expected Output: Environment Readiness Report
Forbidden Output: cambios | instalaciones | inicio de servicios | ejecución
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [PREFLIGHT-ID]
Sesión de planificación, cuando aporte: [PREFLIGHT — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Autoridad: solo lectura

PRECONDICIONES A COMPROBAR
- [RUNTIME O HERRAMIENTA]
- [SERVICIO O DAEMON]
- [ACCESO O PERMISO]

COMPROBACIONES AUTORIZADAS
- consultar versiones y estado;
- comprobar acceso no destructivo;
- identificar contexto conectado;
- registrar evidencia.

NO AUTORIZADO
- crear o modificar archivos;
- instalar o actualizar;
- iniciar, detener o configurar servicios;
- modificar permisos;
- ejecutar la Execution Task.

CONTRATO DE RETORNO
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
Evidencia: [COMANDO, SALIDA O REFERENCIA]
Acción mínima requerida: [ACCIÓN O NINGUNA]
Cambios realizados: Ninguno
```

Un identificador de sesión de preflight es opcional y no impone una política universal de conversaciones de Planning.

Sólo `LISTO PARA EJECUCIÓN` permite aprobar o reanudar escritura.

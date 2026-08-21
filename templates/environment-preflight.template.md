# Environment Preflight

Usa este artefacto cuando una futura Execution Task dependa de una precondición indispensable del entorno que todavía no está comprobada.

```text
Artifact Type: Environment Preflight
Destination Role: Coding Agent — Planning
Expected Output: Environment Readiness Report
Forbidden Output: cambios del entorno | instalaciones | inicio de servicios | ejecución
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [PREFLIGHT-ID]
Sesión de planificación, cuando aporte: [PREFLIGHT — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Autoridad sobre el entorno: solo lectura

PRECONDICIONES A COMPROBAR
- [RUNTIME O HERRAMIENTA]
- [SERVICIO O DAEMON]
- [ACCESO O PERMISO]

COMPROBACIONES AUTORIZADAS
- consultar versiones y estado;
- comprobar acceso no destructivo;
- identificar contexto conectado;
- registrar evidencia.

OUTPUT DELIVERY
- Channel: [Exchange | Conversation | Otro | NO APLICA]
- Location: [outbox | destino lógico | NO APLICA]
- Filename: [PREFLIGHT-ID-READINESS-REPORT.md | OTRO | NO APLICA]
- Caveman Return: [Sí | No]

Si Output Delivery autoriza archivo, puede crearse únicamente el Environment Readiness Report declarado. Ese permiso no autoriza modificar el entorno inspeccionado.

NO AUTORIZADO
- crear o modificar archivos del proyecto o del entorno inspeccionado;
- escribir archivos distintos del output declarado;
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
Cambios al entorno: Ninguno
```

Si `Caveman Return: Sí`, materializa primero el Environment Readiness Report completo y responde en conversación únicamente:

```text
PREFLIGHT: LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
Atención: [DEPENDENCIA/ACCIÓN O NINGUNA]
Reporte: [NOMBRE/PATH]
```

Un identificador de sesión de preflight es opcional y no impone una política universal de conversaciones de Planning.

Sólo `LISTO PARA EJECUCIÓN` permite aprobar o reanudar escritura.

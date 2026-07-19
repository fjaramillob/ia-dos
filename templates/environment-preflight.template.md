# Environment Preflight

```text
Artifact Type: Environment Preflight
Destination Role: Coding Agent — Planning
Expected Output: Environment Readiness Report
Forbidden Output: cambios | instalaciones | inicio de servicios | ejecución
Cycle ID: [CYCLE-ID]
Task ID: [PREFLIGHT-ID]
Agent Session: PREFLIGHT — [RESULTADO]
Cycle Owner: [CONVERSATION SPACE]
Autoridad: solo lectura

PRECONDICIONES A COMPROBAR
- [RUNTIME O HERRAMIENTA]
- [SERVICIO O DAEMON]
- [ACCESO O PERMISO]

COMPROBACIONES AUTORIZADAS
- consultar versiones y estado;
- comprobar acceso no destructivo;
- registrar evidencia.

NO AUTORIZADO
- crear o modificar archivos;
- instalar o actualizar;
- iniciar, detener o configurar servicios;
- ejecutar la Execution Task.

RETORNO
Estado: LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
Dependencia dominante: [ELEMENTO O NINGUNA]
Evidencia: [COMANDO, SALIDA O REFERENCIA]
Acción mínima requerida: [ACCIÓN O NINGUNA]
```

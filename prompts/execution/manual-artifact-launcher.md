# Manual Artifact Launcher

Usa este prompt únicamente cuando un artefacto IA-DOS ya fue construido y materializado como archivo, y la persona necesita indicar manualmente al Coding Agent qué Task consumir.

No es un Artifact Type y no agrega autoridad.

## Patrón preferido

```text
Ejecuta exactamente la tarea definida en:

<PATH-AL-TASK>

Lee el archivo completo antes de actuar y respeta estrictamente su contrato.

Al finalizar materializa el output indicado dentro de la propia tarea y reutiliza exactamente el mismo Task ID.
```

Eso debe bastar cuando la Task ya declara correctamente `Output Delivery`.

## Qué NO debe hacer el launcher

```text
Launcher ≠ Task
Launcher ≠ autorización
Launcher ≠ memoria
Launcher ≠ Exchange
```

No repitas en el launcher:

- objetivo;
- scope;
- Authority Envelope;
- criterios;
- verificaciones;
- condiciones de detención;
- contenido completo del output.

Esos elementos pertenecen a la Task autoritativa.

## Path físico opcional de output

Sólo cuando el path lógico de la Task deba resolverse a una ubicación local concreta, puede agregarse:

```text
Directorio físico correspondiente al output declarado por la Task:
<PATH-A-OUTBOX>
```

Esto no autoriza escribir ningún output que la Task no haya declarado.

## Caveman Return

Si la Task declara `Caveman Return: Sí` y el output completo fue materializado correctamente, responde únicamente con el retorno mínimo definido por la Task, por ejemplo:

```text
EJECUCIÓN: COMPLETADO
Atención requerida: Ninguna
Reporte: <PATH>
```

No repitas tests, commits, deploy, smoke ni detalle que ya vive en el Report.

Si falta la declaración o falla la materialización, devuelve el output completo según el contrato de la Task.

## Exchange

Este launcher puede usarse con Exchange manual, pero Exchange sigue siendo opcional, provider-agnostic, filesystem-first y pasivo.

No uses Manual Artifact Launcher para routing entre Conversation Spaces.
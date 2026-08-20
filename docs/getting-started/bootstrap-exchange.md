# Crear o conectar Exchange Protocol v0

Exchange es opcional. Su función es conservar fuera de las conversaciones el historial operacional de `Execution Task` y `Execution Report` cuando eso aporta continuidad, trazabilidad o independencia del chat del coding agent.

No es memoria durable, backlog ni automatización.

## Cuándo adoptarlo

Exchange suele aportar cuando:

- una Execution Cell ya acumula varias tareas;
- se quiere poder renovar una conversación del coding agent sin perder el historial de instrucciones y retornos;
- varios agentes o herramientas podrían ejecutar la misma línea de trabajo en momentos distintos;
- se necesita una evidencia durable de qué se pidió y qué respondió el ejecutor;
- conservar TASK/REPORT fuera del chat reduce una dependencia operacional relevante.

No lo adoptes sólo porque IA-DOS lo soporta.

## Alcance de v0

El flujo vigente cubre exclusivamente:

```text
Execution Task
        ↓
Execution Report
```

Planning Task, Implementation Plan, backlog, decisiones y memoria durable permanecen fuera del almacén Exchange por defecto.

## Topología recomendada

Una estructura simple es:

```text
proyecto-exch/
├── inbox/
├── outbox/
├── archive/
└── templates/
    ├── TASK.md
    └── REPORT.md
```

La ubicación es una decisión del proyecto. Puede ser una carpeta local, repositorio independiente, subdirectorio de un monorepo u otro almacenamiento durable equivalente.

No crees un repositorio separado si esa separación no aporta valor.

## Semántica de carpetas

### `inbox/`

Contiene TASK preparados para transferir o que todavía forman parte del flujo activo.

Estar en `inbox/` no concede permisos adicionales y no implica que un agente los haya ejecutado.

### `outbox/`

Contiene REPORT devueltos por el ejecutor y pendientes de revisión del Cycle Owner.

Un REPORT en `outbox/` no está aprobado por su mera ubicación.

### `archive/`

Conserva intercambios ya revisados y retirados del flujo activo.

Archivar no significa necesariamente aprobar. También pueden archivarse resultados bloqueados, revertidos o sustituidos después de que exista una decisión explícita.

### `templates/`

Conserva la copia adoptada de los perfiles Exchange utilizados por el proyecto.

Al crear Exchange desde IA-DOS, copia:

```text
templates/exchange-task-v0.template.md
→ proyecto-exch/templates/TASK.md

templates/exchange-report-v0.template.md
→ proyecto-exch/templates/REPORT.md
```

La copia queda asociada a la versión de IA-DOS adoptada por el proyecto. No la actualices silenciosamente cuando cambie `main`.

## Identificación

Cada TASK puede generar su ID sin consultar estado compartido:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

Ejemplo:

```text
PORTAL-20-APP-20260820-164500
```

Archivos activos:

```text
PORTAL-20-APP-20260820-164500-TASK.md
PORTAL-20-APP-20260820-164500-REPORT.md
```

El REPORT reutiliza exactamente el mismo `Task ID`.

No crees `REGISTRY.md`, contador compartido, secuencia global ni sufijos anti-colisión en v0.

## Flujo manual

```text
Conversation Space
        ↓ genera TASK
inbox/
        ↓ copiar / pegar manualmente
Execution Cell
        ↓ responde con REPORT
outbox/
        ↓ revisión
Cycle Owner
        ↓ cierre, corrección o escalamiento
archive/
```

La respuesta del coding agent puede seguir ocurriendo normalmente en su conversación. Mientras Exchange sea manual, copiar ese resultado al archivo REPORT forma parte de la operación humana o conversacional del flujo.

## No sobrescribir historia

Una vez que un TASK fue transferido al ejecutor, no lo edites silenciosamente para cambiar lo que supuestamente se pidió.

Cuando una corrección necesite nuevas instrucciones:

- conserva el TASK y REPORT anteriores;
- registra la nueva instrucción según la política adoptada por el proyecto;
- no borres evidencia para simplificar el historial.

Exchange v0 no impone todavía un esquema de versiones para correcciones.

## Archivo recomendado

Cuando el volumen lo justifique:

```text
archive/
└── YYYY/
    └── MM/
        └── {TASK-ID}/
            ├── TASK.md
            └── REPORT.md
```

No es necesario reorganizar el archivo después de cada tarea si el volumen todavía es pequeño.

## Adopción en `.ia-dos.yaml`

Cuando el proyecto usa manifiesto, registra la ubicación real:

```yaml
resources:
  exchange: "[RUTA_O_URL]"

work:
  execution_task_source: "EXCHANGE"
```

Si Exchange no se usa:

```yaml
resources:
  exchange: "NO_APLICA"
```

Exchange puede coexistir con un backlog distinto. Por ejemplo, Issues puede conservar trabajo pendiente mientras Exchange conserva TASK/REPORT ejecutados.

## Seguridad

No guardes en Exchange:

- secretos;
- contraseñas;
- API keys;
- tokens;
- credenciales;
- datos sensibles innecesarios.

Un TASK debe referenciar secretos por nombre o mecanismo seguro cuando sea necesario, no copiar sus valores.

## Lo que v0 no hace

Exchange v0 no:

- observa carpetas automáticamente;
- dispara ejecuciones;
- sincroniza Google Drive;
- hace polling;
- crea tareas al detectar archivos;
- decide el siguiente trabajo;
- consolida memoria durable;
- reemplaza Issues u otro backlog;
- resuelve la política de conversaciones de Planning.

Estas capacidades pueden evaluarse en evoluciones posteriores únicamente después de validar el flujo manual.

## Verificación

Antes de considerar Exchange adoptado, confirma:

- [ ] existe una razón operacional concreta para conservar TASK/REPORT;
- [ ] la ubicación real está identificada;
- [ ] existen `inbox/`, `outbox/`, `archive/` y `templates/` o equivalentes claros;
- [ ] `templates/TASK.md` y `templates/REPORT.md` corresponden a la versión adoptada;
- [ ] el Task ID sigue el esquema elegido por el proyecto;
- [ ] no existe un segundo backlog accidental dentro de Exchange;
- [ ] no se usa Exchange como memoria vigente;
- [ ] no hay secretos;
- [ ] ningún proceso automático fue asumido como existente.

## Resultado esperado

Exchange está correctamente adoptado cuando el proyecto puede conservar un TASK y su REPORT fuera de la conversación sin alterar el contrato de ejecución, duplicar la memoria durable ni convertir el almacén en un sistema de workflow que v0 todavía no define.

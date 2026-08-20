# Execution Cells y Exchange Protocol v0

Este documento define cómo IA-DOS organiza conversaciones de coding agents y cómo conserva las instrucciones y retornos fuera de esas conversaciones.

## Principio

Una conversación de coding agent no representa una tarea, una especialidad profesional ni un Conversation Space de gobierno.

Representa una instancia activa de una **Execution Cell**.

```text
Conversation Space
    gobierna y decide

Execution Cell
    mantiene continuidad de ejecución

Execution Task
    delimita una unidad concreta

Execution Report
    devuelve evidencia
```

## Execution Cell

Una `Execution Cell` es un contexto durable de ejecución definido por proyecto porque separar ese flujo mejora la continuidad del trabajo.

Las células se descubren según el proyecto. IA-DOS no impone una lista universal de `Frontend`, `Backend`, `QA`, `DevOps` u otros especialistas.

Ejemplos válidos:

```text
Proyecto de aplicación
├── App
└── Wiki Sync
```

```text
Proyecto editorial
├── Artículos
├── Noticias
└── Monetización
```

Una competencia técnica distinta no justifica por sí sola una conversación nueva. Ante la duda, reutiliza una célula existente.

## Política de conversaciones

Mantén una sola conversación activa por `Execution Cell` mientras siga respondiendo bien.

No existe un límite artificial por:

- cantidad de tareas;
- antigüedad;
- ciclo;
- número de mensajes.

Renueva la conversación únicamente cuando exista evidencia de degradación, por ejemplo:

- mezcla decisiones antiguas con vigentes;
- arrastra instrucciones obsoletas;
- confunde tareas cerradas con trabajo activo;
- pierde precisión por contaminación de contexto;
- se requiere deliberadamente un contexto limpio.

La renovación crea una nueva instancia de la misma célula, no una célula nueva.

```text
App · 01  → cerrada
App · 02  → activa
```

La continuidad del proyecto no debe depender de conservar la conversación anterior.

## Autorización por tarea

Reutilizar una conversación no acumula permisos.

Cada `Execution Task` vuelve a declarar objetivo, alcance, restricciones, criterios de aceptación y cualquier acción externa autorizada. Una autorización anterior no se hereda automáticamente.

El coding agent no inicia la siguiente tarea por sí mismo.

## Exchange Protocol v0

Cuando un proyecto necesite conservar el intercambio entre el Orchestrator y coding agents fuera de las conversaciones, puede usar una carpeta hermana de Exchange.

Ejemplo:

```text
Proyectos/
└── Proyecto/
    ├── proyecto-app/
    ├── proyecto-wiki/
    └── proyecto-exch/
        ├── inbox/
        ├── outbox/
        ├── archive/
        └── templates/
```

En v0, Exchange es únicamente un **almacén de instrucciones y respuestas**. No sustituye:

- la implementación;
- la memoria durable;
- el backlog;
- las decisiones de gobierno.

## Identificadores

Cada intercambio usa un identificador autocontenido que no requiere un registro central:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

Ejemplo:

```text
PROPACTO-10-APP-20260819-230215
```

El par documental conserva exactamente el mismo ID:

```text
PROPACTO-10-APP-20260819-230215-TASK.md
PROPACTO-10-APP-20260819-230215-REPORT.md
```

El título humano de la acción vive dentro del archivo y no forma parte del ID.

## Flujo manual v0

```text
Conversation Space
        ↓
Execution Task
        ↓
exchange/inbox
        ↓
transferencia manual
        ↓
Execution Cell
        ↓
Execution Report
        ↓
exchange/outbox
        ↓
Conversation Space revisa
        ↓
archive
```

La transferencia manual es intencional en v0. Sincronización por carpetas, Google Drive, watchers y activación automática pertenecen a evoluciones posteriores.

## Archivo histórico

`TASK` y `REPORT` pueden conservarse indefinidamente como historial operacional.

Cuando un intercambio se cierre, puede archivarse como:

```text
archive/
└── YYYY/
    └── MM/
        └── {EXCHANGE-ID}/
            ├── TASK.md
            └── REPORT.md
```

Una corrección no debe borrar la historia previa. Puede agregarse como artefacto adicional dentro del mismo intercambio.

## Relación con la memoria durable

Exchange responde:

> ¿Qué se pidió y qué respondió el ejecutor?

La Wiki responde:

> ¿Qué conocimiento vigente y confirmado debe reutilizar el proyecto?

La implementación responde:

> ¿Qué está realmente materializado?

Las conversaciones responden:

> ¿Qué estamos razonando o ejecutando ahora?

No uses Exchange como una tercera fuente de verdad.

## Wiki Sync

Una célula `Wiki Sync` puede existir cuando la Wiki tenga repositorio propio y el trabajo físico de sincronización sea recurrente.

Su función debe ser principalmente mecánica:

- alinear archivos locales y remotos;
- revisar Git;
- commit o push cuando esté autorizado;
- validar estructura, Markdown o enlaces.

La síntesis de conocimiento durable permanece bajo el Project Orchestrator y, cuando existe, `90 — Wiki y memoria`.

## Regla principal

```text
Conversation ≠ Task
Conversation ≠ Specialist

Conversation = instancia activa de una Execution Cell

TASK + REPORT = intercambio durable
Wiki = memoria durable
Repositorio = implementación
```

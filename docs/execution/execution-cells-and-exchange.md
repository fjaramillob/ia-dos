# Execution Cells y Exchange Protocol v0

Este documento define cómo IA-DOS organiza conversaciones persistentes de coding agents y cómo puede conservar instrucciones y retornos fuera de esas conversaciones.

## Principio

Una conversación de coding agent no representa una tarea, una especialidad profesional ni un Conversation Space de gobierno.

Representa una instancia activa de una **Execution Cell** cuando el proyecto adopta ese modelo.

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

Ejemplos genéricos válidos:

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

Cada `Execution Task` vuelve a declarar objetivo, alcance, fuera de alcance, autoridad, restricciones, capacidades autorizadas, criterios de aceptación, verificaciones y condiciones de detención suficientes para esa unidad. Una autorización anterior no se hereda automáticamente.

El coding agent no inicia la siguiente tarea por sí mismo.

## Exchange Protocol v0

Exchange es un **perfil opcional de identificación, persistencia y transporte** para artefactos que ya tienen un tipo semántico definido por IA-DOS.

No crea un segundo contrato de Execution Task ni de Execution Report.

```text
Execution Task
    define qué puede ejecutarse y bajo qué límites

Exchange Protocol v0
    define cómo identificar, conservar y transferir TASK/REPORT
```

Cuando un proyecto necesite conservar el intercambio entre el Orchestrator y coding agents fuera de las conversaciones, puede usar un almacén hermano de Exchange.

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

Esta topología es opcional. IA-DOS no exige un repositorio o carpeta Exchange para todos los proyectos.

En v0, Exchange es únicamente un almacén de instrucciones y respuestas. No sustituye:

- la implementación;
- la memoria durable;
- el backlog;
- las decisiones de gobierno;
- el contrato semántico de los artefactos.

## Identificadores

Cada intercambio puede usar un identificador autocontenido que no requiere un registro central:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

Ejemplo genérico:

```text
PORTAL-10-APP-20260819-230215
```

El par documental conserva exactamente el mismo `Task ID`:

```text
PORTAL-10-APP-20260819-230215-TASK.md
PORTAL-10-APP-20260819-230215-REPORT.md
```

El título humano de la acción vive dentro del archivo y no forma parte del ID.

Cuando no existe un `Cycle ID` independiente:

```text
Cycle ID: NO APLICA
Task ID: PORTAL-10-APP-20260819-230215
```

No inventes un ciclo para utilizar Exchange.

## Compatibilidad con el contrato canónico

Una tarea almacenada en Exchange sigue declarando:

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
```

Además debe conservar controles operativos suficientes para que la ejecución no dependa de permisos implícitos de la conversación.

El `Execution Cell` identifica continuidad operacional, pero no sustituye `Destination Role` ni `Cycle Owner`.

Consulta [Tipado de artefactos y validación del receptor](../orchestration/typed-artifact-routing.md).

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

La transferencia manual es intencional en v0. Sincronización por carpetas, almacenamiento compartido, watchers y activación automática pertenecen a evoluciones posteriores y no deben asumirse como existentes.

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

Una corrección no debe borrar la historia previa. El proyecto puede conservar un artefacto adicional o generar una nueva tarea según su política; Exchange v0 no impone todavía un mecanismo de versionado de correcciones.

## Relación con la memoria durable

Exchange responde:

> ¿Qué se pidió y qué respondió el ejecutor?

La Wiki responde:

> ¿Qué conocimiento vigente y confirmado debe reutilizar el proyecto?

La implementación responde:

> ¿Qué está realmente materializado?

Las conversaciones responden:

> ¿Qué estamos razonando o ejecutando ahora?

Exchange es evidencia e historial operacional; no debe convertirse en una fuente adicional de estado vigente cuando ese conocimiento ya fue consolidado en la memoria durable o demostrado por la implementación.

## Wiki Sync

Una célula `Wiki Sync` puede existir cuando la Wiki tenga repositorio propio y el trabajo físico de sincronización sea recurrente.

Su función debe ser principalmente mecánica:

- alinear archivos locales y remotos;
- revisar Git;
- realizar commit o push cuando esté autorizado;
- validar estructura, Markdown o enlaces.

La síntesis de conocimiento durable permanece bajo el Project Orchestrator y, cuando existe, `90 — Wiki y memoria`.

## Planificación

Este documento no define todavía una política universal sobre persistencia o renovación de conversaciones de planificación. La planificación conserva su contrato de solo lectura y debe mantenerse separada de la autorización de ejecución.

No infieras a partir de `Execution Cell` que una sesión de planificación debe abrirse o renovarse por cada tarea.

## Regla principal

```text
Conversation ≠ Task
Conversation ≠ Specialist

Execution Cell = continuidad de ejecución
Execution Task = contrato semántico de una unidad
Exchange = identificación + persistencia + transporte opcional
Wiki = memoria durable
Repositorio = implementación
```
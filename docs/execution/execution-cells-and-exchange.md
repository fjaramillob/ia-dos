# Execution Cells y Exchange Protocol v0

Este documento define cómo IA-DOS organiza conversaciones persistentes de coding agents y cómo puede conservar instrucciones y retornos de ejecución fuera de esas conversaciones.

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

Exchange es un **perfil opcional de identificación, persistencia y transporte manual** para el par canónico:

```text
Execution Task
Execution Report
```

En v0, Exchange no intenta cubrir Planning Tasks, Implementation Plans, backlog, decisiones ni otros artefactos. Esos elementos conservan sus propias fuentes y contratos.

Exchange tampoco crea un segundo contrato de Execution Task o Execution Report.

```text
Execution Task
    define qué puede ejecutarse y bajo qué límites

Exchange Protocol v0
    define cómo identificar, conservar y transferir TASK/REPORT
```

Adopta Exchange cuando conservar el intercambio fuera de la conversación aporte valor real, por ejemplo:

- se desea reducir dependencia del historial del coding agent;
- una Execution Cell puede renovarse o cambiar de herramienta;
- se quiere conservar trazabilidad durable de instrucciones y retornos;
- el proyecto ya usa varias tareas de ejecución y resulta útil mantener un historial independiente del chat.

No lo adoptes por ceremonia. Un proyecto pequeño puede operar correctamente sin Exchange.

## Topología opcional

Una organización posible es:

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

La ubicación puede ser otra. Exchange puede vivir como carpeta, repositorio o almacenamiento durable equivalente. IA-DOS no exige que sea hermano de app y Wiki ni que tenga repositorio Git propio.

Cuando se adopte esta estructura:

```text
inbox/
→ TASK preparado para transferir o actualmente en ejecución

outbox/
→ REPORT devuelto y pendiente de revisión del Cycle Owner

archive/
→ intercambio ya revisado y retirado del flujo activo

templates/
→ copia adoptada de los perfiles TASK/REPORT utilizados por el proyecto
```

`archive` significa **fuera del flujo activo**, no necesariamente `aprobado`. Un intercambio bloqueado, corregido, revertido o cerrado por otra decisión también puede archivarse después de que el Cycle Owner lo revise.

Estas carpetas no constituyen una máquina de estados. En v0, mover archivos entre ellas es una acción manual.

## Lo que Exchange no sustituye

Exchange no sustituye:

- la implementación;
- la memoria durable;
- el backlog;
- las decisiones de gobierno;
- el contrato semántico de los artefactos.

Exchange responde principalmente:

> ¿Qué se pidió y qué respondió el ejecutor?

No responde por sí solo:

> ¿Qué es verdad ahora?

ni:

> ¿Qué queda por hacer?

## Identificadores

Cada intercambio puede usar un identificador autocontenido que no requiere registro central:

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

Exchange v0 no define contador compartido, `REGISTRY.md`, sufijo anti-colisión ni coordinación central de IDs. Tampoco introduce una política especial para dos tareas generadas en el mismo segundo.

## Compatibilidad con el contrato canónico

Una tarea almacenada en Exchange sigue declarando:

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
```

Además conserva los controles operativos necesarios para que la ejecución no dependa de permisos implícitos de la conversación.

El `Execution Cell` identifica continuidad operacional, pero no sustituye `Destination Role` ni `Cycle Owner`.

Consulta [Tipado de artefactos y validación del receptor](../orchestration/typed-artifact-routing.md).

## Flujo manual v0

```text
Conversation Space
        ↓ prepara Execution Task
inbox/
        ↓ transferencia manual
Execution Cell
        ↓ devuelve Execution Report
outbox/
        ↓ revisión
Cycle Owner
        ↓
archive/
```

En v0:

- el Conversation Space puede generar el TASK y guardarlo manualmente;
- el usuario puede pegarlo en la conversación adecuada del coding agent;
- el coding agent puede responder normalmente en chat;
- el REPORT puede copiarse manualmente a `outbox/`;
- el Cycle Owner revisa el resultado antes de archivar el intercambio;
- ningún movimiento de archivo ejecuta automáticamente otra acción.

Sincronización por carpetas, almacenamiento compartido, watchers, polling, triggers y activación automática pertenecen a evoluciones posteriores y no deben asumirse como existentes.

## Inmutabilidad histórica

Una vez transferido al ejecutor, no reescribas silenciosamente un TASK para cambiar lo que fue solicitado.

Si una corrección o continuación requiere nuevas instrucciones, conserva el artefacto previo y aplica la política explícita del proyecto. Exchange v0 no impone todavía si esa corrección reutiliza una identidad versionada o crea un Task ID nuevo.

La regla mínima es:

> no sobrescribir historia para hacer parecer que una instrucción anterior fue distinta.

## Archivo histórico

`TASK` y `REPORT` pueden conservarse indefinidamente como historial operacional.

Una organización válida es:

```text
archive/
└── YYYY/
    └── MM/
        └── {EXCHANGE-ID}/
            ├── TASK.md
            └── REPORT.md
```

El proyecto puede conservar artefactos adicionales de corrección cuando sea necesario. Exchange v0 no impone todavía un mecanismo de versionado de correcciones.

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

Cuando un `Execution Report` descubre conocimiento potencialmente durable, el Cycle Owner decide si debe consolidarse en memoria. El REPORT no actualiza la Wiki automáticamente.

## Wiki Sync

Una célula `Wiki Sync` puede existir cuando la Wiki tenga repositorio propio y el trabajo físico de sincronización sea recurrente.

Su función debe ser principalmente mecánica:

- alinear archivos locales y remotos;
- revisar Git;
- realizar commit o push cuando esté autorizado;
- validar estructura, Markdown o enlaces.

La síntesis de conocimiento durable permanece bajo el Project Orchestrator y, cuando aporta, `90 — Wiki y memoria`.

## Planificación

Este documento no define todavía una política universal sobre persistencia o renovación de conversaciones de planificación. La planificación conserva su contrato de solo lectura y debe mantenerse separada de la autorización de ejecución.

Exchange v0 tampoco convierte Planning Task o Implementation Plan en artefactos de su flujo por defecto.

No infieras a partir de `Execution Cell` que una sesión de planificación debe abrirse o renovarse por cada tarea.

## Regla principal

```text
Conversation ≠ Task
Conversation ≠ Specialist

Execution Cell = continuidad de ejecución
Execution Task = contrato semántico de una unidad
Exchange = identificación + persistencia + transporte manual opcional
Wiki = memoria durable
Repositorio = implementación
```

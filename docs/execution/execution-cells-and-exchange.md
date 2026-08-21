# Execution Cells y Exchange

Este documento define cómo IA-DOS organiza conversaciones persistentes de coding agents y cómo puede utilizar una pasarela pasiva de archivos Markdown entre Conversation Agents y Code Agents.

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

Exchange
    sólo transporta/almacena archivos .md entre ambos lados
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

# Exchange

Exchange es una **pasarela pasiva de archivos Markdown**.

No es un protocolo que defina artefactos, IDs, estados, contratos, workflow o decisiones.

No crea otro tipo de Execution Task ni otro tipo de Execution Report.

La responsabilidad se distribuye así:

```text
Conversation Agent
→ construye la Execution Task completa
→ asigna Task ID
→ decide el nombre del archivo .md cuando se materializa

Exchange
→ almacena / pone a disposición ese .md

Code Agent
→ ejecuta la tarea
→ devuelve el Execution Report con el mismo Task ID

Exchange
→ almacena / pone a disposición el REPORT .md

Conversation Agent / Cycle Owner
→ revisa y decide
```

## Qué hace Exchange

Exchange hace únicamente esto:

- recibe archivos `.md` ya construidos;
- los mantiene disponibles para el otro lado;
- conserva el historial cuando el proyecto decide archivarlo.

Exchange no interpreta el contenido del archivo.

## Qué NO hace Exchange

Exchange no:

- genera `Task ID`;
- valida `Task ID`;
- define el formato del ID;
- crea `Execution Task`;
- crea `Execution Report`;
- define estados;
- aprueba resultados;
- decide el siguiente trabajo;
- mantiene backlog;
- consolida memoria durable;
- impone nombres de archivo;
- define versionado de correcciones;
- observa carpetas automáticamente en v0;
- dispara ejecuciones;
- hace polling;
- define watchers o triggers;
- sincroniza servicios externos por sí mismo.

El esquema de identidad pertenece al artefacto construido por el agente conversacional y al contrato de IA-DOS, no a Exchange.

## Topología mínima

Una estructura posible es:

```text
proyecto-exch/
├── inbox/
├── outbox/
└── archive/
```

La ubicación es opcional. Puede ser carpeta local, repositorio, carpeta sincronizada u otro almacenamiento durable equivalente.

No es obligatorio que exista un recurso hermano `proyecto-exch`.

## Semántica operacional de carpetas

Estas carpetas son **ubicaciones de paso**, no estados del método.

```text
inbox/
→ archivos .md que van desde Conversation Agent hacia Code Agent

outbox/
→ archivos .md que vuelven desde Code Agent hacia Conversation Agent

archive/
→ archivos retirados del intercambio activo y conservados como historial
```

Nada ocurre automáticamente por mover un archivo.

`archive/` tampoco significa `APROBADO`; sólo significa que el archivo ya no está en el intercambio activo.

## Artefactos

El archivo enviado por Exchange debe ser exactamente el artefacto que IA-DOS ya habría entregado por chat u otro medio.

Por ejemplo:

```text
Execution Task
→ mismo contenido
→ mismo Task ID
→ mismo contrato
```

Si se guarda como `.md`, el nombre de archivo lo determina el agente o flujo que materializa el artefacto.

IA-DOS recomienda que el nombre permita relacionarlo fácilmente con su `Task ID`, pero Exchange no lo define ni lo valida.

El `Execution Report` devuelve el `Task ID` de la Execution Task original. Esa regla pertenece al contrato del artefacto, no a Exchange.

## Flujo manual v0

```text
Conversation Agent
        ↓ genera Execution Task.md
inbox/
        ↓ transferencia manual
Code Agent / Execution Cell
        ↓ genera Execution Report.md
outbox/
        ↓ transferencia manual
Conversation Agent / Cycle Owner
        ↓ revisión
archive/ cuando corresponda
```

La transferencia manual es intencional en v0.

Una futura sincronización de carpetas puede automatizar la **entrega física** del archivo sin cambiar esta frontera: Exchange seguiría sin definir el contenido o la identidad del artefacto.

## Inmutabilidad histórica

Una vez que un artefacto fue entregado al otro lado, no debe sobrescribirse silenciosamente para alterar qué se pidió o qué se respondió.

Si una corrección requiere un nuevo artefacto, el agente conversacional decide cómo identificarlo según el contrato vigente del proyecto.

Exchange sólo conserva los archivos resultantes.

## Relación con la memoria durable

Exchange responde únicamente:

> ¿Qué archivos intercambiamos?

La Wiki o memoria durable responde:

> ¿Qué conocimiento vigente y confirmado debe reutilizar el proyecto?

La implementación responde:

> ¿Qué está realmente materializado?

El backlog responde:

> ¿Qué trabajo queda por hacer?

Las conversaciones responden:

> ¿Qué estamos razonando o ejecutando ahora?

Exchange no debe convertirse en ninguna de esas fuentes.

## Wiki Sync

Una célula `Wiki Sync` puede existir cuando la Wiki tenga repositorio propio y el trabajo físico de sincronización sea recurrente.

Su función debe ser principalmente mecánica:

- alinear archivos locales y remotos;
- revisar Git;
- realizar commit o push cuando esté autorizado;
- validar estructura, Markdown o enlaces.

La síntesis de conocimiento durable permanece bajo el Project Orchestrator y, cuando aporta, `90 — Wiki y memoria`.

## Planificación

Este documento no define una política universal sobre persistencia o renovación de conversaciones de planificación.

Exchange tampoco decide qué tipos de artefactos puede producir IA-DOS. Si en el futuro se decide transportar otros `.md`, eso no cambia su naturaleza pasiva.

## Regla principal

```text
Conversation ≠ Task
Conversation ≠ Specialist

Execution Cell = continuidad de ejecución
Execution Task = contrato semántico de una unidad
Execution Report = evidencia de retorno
Exchange = pasarela pasiva de archivos .md
Wiki = memoria durable
Repositorio = implementación
```
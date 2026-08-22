# Execution Cells y Exchange

Este documento define cómo IA-DOS organiza continuidad de ejecución en coding agents y cómo puede utilizar una pasarela pasiva de archivos Markdown entre Conversation Agents y Code Agents.

## Principio

Una conversación de coding agent no representa una tarea, una especialidad profesional ni un Conversation Space de gobierno.

Puede representar una instancia activa de una **Execution Cell** cuando el proyecto adopta ese modelo.

```text
Persona responsable
    conserva dirección y aprobación final aplicable

Conversation Space / Cycle Owner
    gobierna dentro de autoridad delegada

Execution Cell
    mantiene continuidad de ejecución

Execution Task
    delimita una unidad concreta y sus permisos

Execution Report
    devuelve evidencia

Exchange
    sólo transporta o almacena archivos .md entre Conversation Agent y Coding Agent cuando se adopta ese transporte
```

## Execution Cell

Una `Execution Cell` es un contexto durable de ejecución definido por proyecto porque separar ese flujo mejora continuidad operacional.

Las células se descubren según el proyecto. IA-DOS no impone una lista universal de `Frontend`, `Backend`, `QA`, `DevOps` u otros especialistas.

Ejemplos genéricos:

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

Mantén una sola conversación activa por Execution Cell mientras siga respondiendo bien.

No existe un límite artificial por:

- cantidad de tareas;
- antigüedad;
- ciclo;
- número de mensajes;
- tiempo transcurrido.

Renueva únicamente ante evidencia de degradación, por ejemplo:

- mezcla decisiones antiguas con vigentes;
- arrastra instrucciones obsoletas;
- confunde tareas cerradas con trabajo activo;
- pierde precisión por contaminación de contexto;
- se requiere deliberadamente un contexto limpio.

La renovación crea una nueva instancia de la misma célula:

```text
App · 01 → cerrada
App · 02 → activa
```

La continuidad del proyecto no debe depender de conservar la conversación anterior.

## Autorización por tarea

Reutilizar una conversación no acumula permisos.

Cada Execution Task vuelve a declarar:

- objetivo;
- alcance y fuera de alcance;
- autoridad y acceso;
- capacidades autorizadas;
- acciones externas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención;
- destino del reporte.

El coding agent no inicia la siguiente tarea por sí mismo.

## Relación con Planning

Execution Cells no definen una política para conversaciones de Planning.

Un identificador lógico `PLAN — ...` puede utilizarse cuando aporte, pero IA-DOS mantiene abierta la política universal sobre persistencia o renovación de conversaciones de Planning.

La separación entre Planning y Execution es de rol y autoridad. Una futura Execution Task puede reutilizar una Execution Cell activa y debe volver a declarar permisos completos.

# Exchange

Exchange es una **pasarela pasiva y opcional de archivos Markdown entre Conversation Agents y Coding Agents**.

No es un protocolo semántico y no define artefactos, IDs, estados, contratos, workflow o decisiones.

## Exchange no enruta Conversation Spaces

El routing entre Conversation Spaces no usa Exchange por defecto.

```text
Conversation Space → Conversation Space
→ Specialist Handoff inline, autocontenido y copiable
→ la persona lo pega como mensaje en el espacio destino

Conversation Space → Coding Agent
→ Task / Preflight / Resume
→ puede usar `.md` y Exchange cuando el proyecto adopta ese transporte
```

Por tanto, un `Specialist Handoff` no requiere:

- `.md`;
- `inbox/`;
- `outbox/`;
- path absoluto;
- `Manual Artifact Launcher`.

Una copia documental del handoff sólo puede considerarse archivo auxiliar solicitado explícitamente o convención local separada; no es la transferencia normativa entre espacios.

```text
Conversation Agent
→ construye la Execution Task completa
→ asigna Task ID
→ decide el filename si materializa el artefacto

Exchange
→ almacena / pone a disposición ese .md

Code Agent / Execution Cell
→ ejecuta la tarea
→ construye Execution Report con el mismo Task ID

Exchange
→ almacena / pone a disposición el REPORT .md

Conversation Agent / Cycle Owner
→ revisa evidencia dentro de autoridad delegada

Persona responsable
→ aprueba cuando corresponde
```

## Qué hace Exchange

Únicamente:

- recibe archivos `.md` ya construidos destinados a intercambio con Coding Agents;
- los mantiene disponibles para el otro lado;
- puede conservar historial cuando el proyecto decide archivarlo.

Exchange no interpreta el contenido.

## Qué NO hace Exchange

Exchange no:

- enruta entre Conversation Spaces;
- materializa por defecto Specialist Handoffs;
- genera o valida Task IDs;
- define formato de IDs;
- crea Execution Tasks o Execution Reports;
- define filenames;
- define templates;
- define estados;
- concede permisos;
- aprueba resultados;
- decide siguiente trabajo;
- mantiene backlog;
- consolida memoria durable;
- define versionado de correcciones;
- observa carpetas automáticamente;
- dispara ejecuciones;
- hace polling;
- define watchers o triggers;
- sincroniza servicios externos por sí mismo.

La identidad pertenece al artefacto construido por el Conversation Agent y al contrato de IA-DOS.

## Topología mínima

Una estructura posible es:

```text
proyecto-exch/
├── inbox/
├── outbox/
└── archive/
```

La ubicación es opcional. Puede ser carpeta local, repositorio, carpeta sincronizada u otro almacenamiento adecuado.

No es obligatorio un recurso hermano `proyecto-exch`.

## Semántica de carpetas

Son ubicaciones físicas, no estados del método.

```text
inbox/
→ archivos .md hacia Code Agent

outbox/
→ archivos .md hacia Conversation Agent

archive/
→ archivos retirados del intercambio activo y conservados como historia
```

Nada ocurre automáticamente por mover un archivo.

`archive/` no significa `APROBADO` ni `COMPLETADO`.

## Artefactos

El archivo enviado por Exchange es exactamente el artefacto que IA-DOS habría entregado por otro medio al Coding Agent.

```text
Execution Task
→ mismo contenido
→ mismo Task ID
→ mismo contrato
```

El filename lo decide el agente o flujo que materializa el archivo. IA-DOS puede recomendar relacionarlo con Task ID, pero Exchange no lo define ni valida.

El Execution Report reutiliza el Task ID de la Execution Task original por contrato del artefacto.

## Flujo manual actual

```text
Conversation Agent
        ↓ construye TASK.md
inbox/
        ↓ transferencia
Code Agent / Execution Cell
        ↓ construye REPORT.md
outbox/
        ↓ transferencia
Conversation Agent / Cycle Owner
        ↓ revisión
archive/ cuando corresponda
```

La transferencia puede ser manual. Una futura sincronización física no cambia la naturaleza pasiva de Exchange y no autoriza watchers, triggers o ejecución automática por sí misma.

### Manual Artifact Launcher

Cuando la persona necesita iniciar manualmente al Code Agent, puede usar un `Manual Artifact Launcher` efímero que indique:

- tipo esperado;
- ruta física del artefacto autoritativo en `inbox/`;
- ruta física de `outbox/` cuando la tarea autorice materializar la salida;
- instrucción de leer el artefacto completo.

El launcher **no es un Artifact Type** y no agrega autoridad ni elige el modo de retorno.

```text
Launcher = localización manual para Coding Agent
Artifact = contrato autoritativo
Exchange = almacenamiento pasivo
```

No uses Manual Artifact Launcher para un Specialist Handoff entre Conversation Spaces.

Consulta [Entrega manual de artefactos](manual-artifact-delivery.md) y el [prompt reusable](../../prompts/execution/manual-artifact-launcher.md).

### Materialización del output

Una tarea puede autorizar explícitamente que su output completo se escriba como `.md` en `outbox/`.

Esto no convierte Exchange en un sistema activo ni amplía escritura sobre el proyecto.

En Planning y Preflight:

```text
solo lectura del proyecto/entorno
≠ prohibición de materializar el propio output autorizado
```

El Code Agent puede escribir únicamente el artefacto de salida declarado y sólo en el destino autorizado.

### Caveman Return

La respuesta conversacional del Code Agent puede reducirse a un `Caveman Return` **sólo cuando**:

1. la Task autoritativa declara `Caveman Return: Sí`;
2. el output completo fue materializado correctamente en el destino declarado.

```text
estado o resultado esencial
+ atención requerida
+ nombre/path del artefacto completo
```

Si cualquiera de esas condiciones falta, el Code Agent devuelve el artefacto completo según el canal y contrato de la Task.

El Caveman Return es una representación conversacional mínima, **no un nuevo artefacto** y no reemplaza el Implementation Plan, Environment Readiness Report o Execution Report completo.

## Inmutabilidad histórica

Una vez entregado un artefacto, no debe sobrescribirse silenciosamente para alterar qué se pidió o respondió.

Si una corrección requiere un nuevo artefacto, el agente responsable decide su identidad según las reglas vigentes del proyecto. Exchange sólo conserva el archivo resultante.

## Relación con memoria, backlog e implementación

```text
Exchange
→ ¿qué archivos intercambiamos con Coding Agents?

LLM Wiki / memoria durable
→ ¿qué conocimiento vigente y reusable conservamos?

Repository
→ ¿qué está materializado?

Backlog
→ ¿qué trabajo queda?

Conversations
→ ¿qué estamos razonando o gobernando ahora?
```

Exchange no debe convertirse en ninguna de esas fuentes.

`memoria durable` es la responsabilidad funcional. `LLM Wiki` es una posible materialización portable de esa memoria.

## Wiki Sync

Una célula `Wiki Sync` puede existir cuando el mantenimiento físico de una LLM Wiki sea un flujo durable que justifique continuidad separada.

Su función puede ser principalmente mecánica:

- alinear archivos locales/remotos;
- revisar Git;
- commit o push cuando esté autorizado;
- validar estructura, Markdown o enlaces.

La síntesis de conocimiento permanece en el plano conversacional y puede involucrar `90 — Wiki y memoria` cuando aporta.

No crees `Wiki Sync` automáticamente por usar una LLM Wiki.

## Regla principal

```text
Conversation ≠ Task
Conversation ≠ Execution Cell
Execution Cell ≠ Specialist

Conversation Space Handoff = inline y copiable
Execution Cell = continuidad de ejecución
Execution Task = contrato de una unidad
Execution Report = evidencia
LLM Wiki = memoria durable materializada
Repository = implementación
Exchange = pasarela pasiva de archivos .md hacia/desde Coding Agents
Manual Artifact Launcher = localización efímera para Coding Agent, no autoridad
Caveman Return = presentación conversacional mínima sólo por opt-in de la Task
Persona responsable = aprobación final aplicable
```

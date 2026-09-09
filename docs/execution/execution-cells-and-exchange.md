# Execution Cells y Exchange

Este documento define continuidad de ejecución en coding agents y la pasarela opcional de artefactos Markdown que un proyecto puede usar para desacoplar Conversation Agents y Coding Agents.

## Principio

```text
Persona responsable
    conserva dirección y aprobación final aplicable

Conversation Space / Cycle Owner
    gobierna dentro de autoridad delegada

Execution Cell
    mantiene continuidad de ejecución

Execution Task
    delimita un outcome cohesivo y su Authority Envelope

Execution Report
    devuelve evidencia de lo ocurrido

Exchange
    transporta o almacena artefactos .md hacia/desde Coding Agents cuando el proyecto lo adopta
```

## Execution Cell

Una `Execution Cell` es un contexto de continuidad de ejecución definido por proyecto porque separar ese flujo mejora continuidad operacional.

No representa una tarea, una especialidad profesional ni un Conversation Space.

Mantén una sola conversación activa por Execution Cell mientras siga respondiendo bien. No existe un límite artificial por cantidad de tareas, antigüedad, ciclo, mensajes o tiempo transcurrido.

Renueva únicamente ante evidencia de degradación, contaminación de contexto o necesidad real de un contexto limpio.

Reutilizar una conversación no acumula permisos. Cada Execution Task vuelve a declarar su Authority Envelope.

## Tareas largas y checkpoints

Una Task puede durar lo necesario para completar un outcome cohesivo bajo una frontera estable de autoridad.

Cuando la continuidad operacional lo justifique puede existir un sidecar opcional:

```text
<TASK-ID>-CHECKPOINT.md
```

Puede registrar:

- avance;
- HEAD o referencia técnica equivalente;
- estado del worktree;
- fases completadas;
- pendiente;
- bloqueos;
- evidencia de continuidad útil para otro Coding Agent.

```text
Checkpoint ≠ autorización
Checkpoint ≠ Execution Resume
Checkpoint ≠ Artifact Type
```

La autoridad sigue estando en la Execution Task y, cuando corresponde, en Execution Resume. Un nuevo Coding Agent debe leer Task + Checkpoint, verificar el estado real y continuar sólo dentro de la autoridad vigente.

## Wiki Sync

Una célula `Wiki Sync` puede existir cuando el mantenimiento físico de una LLM Wiki sea un flujo durable que justifique continuidad separada.

Su función puede ser principalmente mecánica:

- alinear archivos locales/remotos;
- revisar Git;
- commit o push cuando estén explícitamente autorizados en la Task;
- validar estructura, Markdown o enlaces.

La síntesis de conocimiento permanece en el plano conversacional y puede involucrar `90 — Wiki y memoria` cuando aporta.

No crees `Wiki Sync` automáticamente por usar una LLM Wiki y no confundas esa célula con memoria durable o autoridad adicional.

# Exchange

Exchange es una **pasarela opcional, provider-agnostic, filesystem-first y pasiva de artefactos Markdown hacia/desde Coding Agents**.

No es un protocolo semántico, workflow engine, backlog, memoria durable ni router conversacional.

```text
Exchange ≠ Google Drive
Exchange ≠ workflow engine
Exchange ≠ backlog
Exchange ≠ memoria durable
Exchange ≠ router entre Conversation Spaces
```

Google Drive puede ser un adaptador de sincronización opcional. También pueden usarse OneDrive, Dropbox, Syncthing, NAS, una carpeta local/manual u otro mecanismo equivalente. Ninguno de esos proveedores cambia la semántica de Exchange.

## Exchange no enruta Conversation Spaces

```text
Conversation Space → Conversation Space
→ Specialist Handoff inline, autocontenido y copiable

Conversation Space → Coding Agent
→ Planning Task | Environment Preflight | Execution Task | Execution Resume
→ chat o `.md`/Exchange según el contrato de entrega
```

Un `Specialist Handoff` no requiere `.md`, `inbox/`, `outbox/`, path absoluto ni `Manual Artifact Launcher`.

## Qué hace Exchange

Únicamente:

- mantiene artefactos Markdown disponibles para el otro lado;
- permite desacoplar el intercambio del historial conversacional;
- puede conservar artifacts retirados de circulación activa por trazabilidad.

Exchange no interpreta contenido ni decide qué ejecutar.

## Qué NO hace Exchange

Exchange no:

- enruta entre Conversation Spaces;
- genera o valida Task IDs;
- define filenames o templates;
- define Artifact Types;
- define estados de workflow;
- concede permisos;
- aprueba resultados;
- decide siguiente trabajo;
- mantiene backlog;
- consolida memoria durable;
- observa carpetas automáticamente;
- dispara ejecuciones;
- hace polling;
- define watchers o triggers;
- sincroniza servicios externos por sí mismo.

## Topología mínima

```text
project-exch/
├── inbox/
├── outbox/
└── archive/
```

La ubicación es opcional. No es obligatorio un repositorio hermano `project-exch`.

## Semántica de carpetas

```text
inbox/
→ artifacts operativamente activos destinados a Coding Agents

outbox/
→ outputs pendientes de consumo o todavía requeridos por trabajo activo

archive/
→ cold storage operacional de artifacts retirados de circulación activa pero conservados por trazabilidad
```

Reglas:

```text
folder ≠ workflow state
archive ≠ aprobado
archive ≠ completado
archive ≠ memoria durable
archive ≠ repositorio de documentos vivos
```

Mover un archivo no cambia estado, autoridad ni aprobación.

Un documento vivo —por ejemplo un documento jurídico en construcción— no debe usar `archive/` como repositorio documental por defecto.

## Flujo manual

```text
Conversation Agent
→ construye artefacto autoritativo
→ lo materializa en inbox cuando la Task/flujo lo requiere

Persona
→ puede entregar un Manual Artifact Launcher

Code Agent / Execution Cell
→ consume el artefacto
→ ejecuta dentro de autoridad
→ materializa el output autorizado en outbox

Conversation Agent / Cycle Owner
→ consume y revisa el output completo

archive/
→ sólo cuando el artifact deja la circulación activa y se conserva por trazabilidad
```

Nada ocurre automáticamente por la existencia o movimiento de un archivo.

## Manual Artifact Launcher

El launcher es efímero y no autoritativo. Patrón preferido:

```text
Ejecuta exactamente la tarea definida en:
<PATH-AL-TASK>

Lee el archivo completo antes de actuar y respeta estrictamente su contrato.
Al finalizar materializa el output indicado dentro de la propia tarea y reutiliza exactamente el mismo Task ID.
```

```text
Launcher ≠ Task
Launcher ≠ autorización
Launcher ≠ memoria
Launcher ≠ Exchange
```

## Output Delivery y Caveman Return

Una Task puede autorizar:

```text
Output Delivery:
Channel: Exchange
Location: outbox
Filename: <TASK-ID>-REPORT.md
Caveman Return: Sí
```

Sólo esa declaración autoriza materializar el output indicado.

Si el output completo fue materializado correctamente y la Task declara `Caveman Return: Sí`, la conversación debe ser mínima:

```text
EJECUCIÓN: COMPLETADO
Atención requerida: Ninguna
Reporte: <PATH>
```

No repitas tests, commits, deploy, smoke ni detalle que ya vive en el Report.

Caveman Return no es un Artifact Type y nunca sustituye un output completo que no haya sido materializado correctamente.

## Inmutabilidad histórica

Una vez entregado un artefacto, no debe sobrescribirse silenciosamente para alterar qué se pidió o respondió.

Si una corrección requiere un nuevo artefacto, su identidad se decide según las reglas vigentes del proyecto. Exchange sólo conserva el archivo resultante.

## Relación con otras fuentes

```text
Exchange
→ ¿qué artifacts operativos intercambiamos con Coding Agents?

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

## Regla principal

```text
Execution Cell = continuidad de ejecución
Execution Task = outcome cohesivo + Authority Envelope
Execution Checkpoint = continuidad operacional, no autoridad
Execution Report = evidencia
Exchange = pasarela pasiva opcional de artifacts .md hacia/desde Coding Agents
Manual Artifact Launcher = localización efímera
Caveman Return = presentación mínima después de materialización completa autorizada
```
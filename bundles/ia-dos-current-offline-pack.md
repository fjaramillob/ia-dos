# IA-DOS Current Offline Pack

**Estado:** VIGENTE

**Baseline canónico:** `IA-DOS v0.1.0-alpha.3 — adopción real / ejecución cohesiva 2026-09-09`

**Uso:** onboarding y operación cuando el asistente no puede navegar `https://github.com/fjaramillob/ia-dos`.

Este es el único bundle vigente para nuevos onboardings offline. No lo combines con bundles históricos. Si el repositorio canónico está accesible, éste prevalece.

## Modelo

```text
Persona responsable = dirección y aprobación final aplicable
Conversation Space = gobierno dentro de autoridad delegada
Specialist Handoff = transferencia inline y copiable entre Conversation Spaces
Execution Cell = continuidad de ejecución
Execution Task = outcome cohesivo bajo frontera estable de autoridad
Authority Envelope = permisos explícitos dentro de Execution Task
Execution Checkpoint = continuidad operacional, no autoridad
Execution Report = evidencia de lo ocurrido
Memoria durable = responsabilidad funcional
LLM Wiki = materialización durable, portable y navegable
Repository = implementación real
Exchange = pasarela pasiva opcional hacia/desde Coding Agents
```

`Authority Envelope` y `Execution Checkpoint` no son Artifact Types.

## Responsabilidad humana

La persona responsable define propósito, prioridad, restricciones y autoridad.

Project Orchestrator y Cycle Owner gobiernan dentro de autoridad delegada. La persona responsable interviene cuando una decisión cambia materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

El coding agent no aprueba su propio plan o ejecución.

## Inicio y continuidad

Usa `00 — Dirección y orquestación` como Conversation Space inicial canónico.

- producto nuevo → `definición inicial`;
- producto existente → `descubrimiento y adopción`.

Los Conversation Spaces no son etapas. Abre otro sólo cuando una brecha de dominio requiera contexto persistente propio.

Si un Conversation Space es nuevo, se retoma después de un cambio relevante de IA-DOS o muestra reglas obsoletas, consulta la referencia vigente antes de decidir. No reinicies onboarding ni releas todo el framework por defecto; carga sólo los contratos necesarios.

## Handoff entre Conversation Spaces

```text
Conversation Space origen
→ Specialist Handoff inline, autocontenido y copiable
→ persona copia/pega
→ Conversation Space destino
```

No requiere `.md`, Exchange, inbox/path ni Manual Artifact Launcher.

Si el proyecto usa Exchange, el handoff puede declarar:

```text
Este proyecto adopta Exchange para artifacts hacia/desde Coding Agents.
No lo uses para routing entre Conversation Spaces.
```

## Gate de avance

```text
1. ¿El resultado está definido, es cohesivo, acotado y verificable bajo una frontera estable de autoridad?
2. Si depende de historia, ¿la memoria necesaria ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿corresponde Planning?
```

- historia indispensable sólo en chats → Memory Bootstrap Gate;
- readiness desconocido → Environment Preflight;
- falta inspección/diseño → Planning Task;
- outcome listo → Execution Task;
- brecha de otro dominio → Specialist Handoff;
- decisión material fuera de autoridad → deriva sólo esa decisión;
- reorientación → escala a `00`.

## Memory Bootstrap Gate

```text
PASS
→ continúa

BOOTSTRAP REQUIRED
→ bloquea la unidad dependiente original
→ materializa checkpoint durable mínimo mediante Execution Task separada
→ revisa Report
→ reevalúa gate original
```

No uses edad, número de mensajes, tareas o porcentajes como umbral.

## Planning Task e Implementation Plan

Planning es de solo lectura respecto del proyecto/entorno inspeccionado y produce Implementation Plan.

El plan propone, no ejecuta ni se autoaprueba.

No todo Implementation Plan requiere automáticamente una nueva aprobación humana. El Cycle Owner puede adoptarlo dentro de autoridad ya delegada. La persona responsable interviene cuando cambia materialmente dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante.

## Environment Preflight

Se usa cuando una futura Execution Task depende de una precondición indispensable no comprobada.

Produce:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

Sólo `LISTO PARA EJECUCIÓN` permite considerar escritura.

## Granularidad de Execution Task

IA-DOS no maximiza cantidad de Tasks; maximiza el resultado seguro y verificable por Task.

Una Execution Task persigue un **outcome definido, cohesivo, acotado y verificable bajo una frontera estable de autoridad**.

No dividas sólo por:

- duración;
- cantidad de archivos o comandos;
- implementación;
- tests;
- commit;
- push;
- deploy;
- smoke.

Puede contener:

```text
Revalidate
→ Implement
→ Verify
→ Commit
→ Push
→ Deploy
→ Production Smoke
→ Final State
```

si todas las fases sirven al mismo outcome y están autorizadas.

Divide o detén cuando cambie materialmente outcome, scope, autoridad, arquitectura, seguridad, datos, riesgo, coste o entorno.

## Authority Envelope

La propia Execution Task agrupa permisos explícitos para el outcome completo.

Ejemplo:

```text
Code:
- escritura autorizada en scope

Git:
- stage selectivo
- commit
- push fast-forward

Delivery:
- deployment mediante mecanismo existente

Production:
- smoke autorizado

No autorizado:
- schema
- nuevos servicios
- costes
- force push
- cambios fuera del scope
```

Regla:

```text
acción sensible no declarada
→ no autorizada

acción declarada + gates cumplidos + frontera estable
→ no requiere otra ida y vuelta humana por rutina

cambio material de frontera
→ STOP y nueva decisión
```

El coding agent no aprueba su propio plan o ejecución.

## Compresión de contexto

```text
referencias de autoridad
+ delta del ciclo
+ contrato operativo explícito
```

Distingue:

```text
Embedded Contract
→ debe viajar dentro de la Task

Required Reading
→ documentos concretos que el Coding Agent debe leer

Reference
→ trazabilidad/navegación; no implica lectura por defecto
```

Una Task es suficientemente autocontenida cuando:

```text
Task + Required Reading
→ permiten ejecutar correctamente sin conversaciones previas
```

No repitas por rutina Implementation Plan completo, Wiki completa, reportes previos, contrato factual completo o historia del proyecto.

Permisos, límites, seguridad, criterios y stop conditions permanecen explícitos.

## Execution Cell y Checkpoint

Una Execution Cell conserva continuidad, no permisos.

Una Task larga o un cambio de Coding Agent puede usar opcionalmente:

```text
<TASK-ID>-CHECKPOINT.md
```

Puede registrar avance, HEAD, worktree, fases completadas, pendiente y bloqueos.

```text
Checkpoint ≠ autorización
Checkpoint ≠ Artifact Type
```

Un nuevo Coding Agent lee Task + Checkpoint, verifica estado real y continúa dentro de la autoridad vigente.

## Execution Resume

```text
Execution Resume
= Task original
+ delta del bloqueo resuelto
```

Conserva Task ID y sólo aplica si objetivo, scope, autoridad, seguridad y arquitectura siguen sin cambios.

## Execution Report

```text
Task
→ qué estaba autorizado

Report
→ qué ocurrió realmente
```

El Report es evidence-first y proporcional.

Estructura preferente:

```text
Artifact Type
Task ID
Estado
Atención requerida

Outcome
Evidence
Actual Scope
Acceptance
Deviations
Final State
```

Agrega otras secciones sólo cuando aporten evidencia real. No vuelvas a narrar la Task.

Estados:

```text
COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
```

El Report no aprueba su propio resultado, no elige la siguiente unidad y no consolida memoria durable por defecto.

## Exchange

Exchange es **opcional, provider-agnostic, filesystem-first y pasivo**.

```text
Exchange ≠ Google Drive
Exchange ≠ workflow engine
Exchange ≠ backlog
Exchange ≠ memoria durable
Exchange ≠ router entre Conversation Spaces
```

Puede usar Google Drive, OneDrive, Dropbox, Syncthing, NAS, carpeta local/manual u otro mecanismo equivalente como transporte físico.

Topología mínima:

```text
project-exch/
├── inbox/
├── outbox/
└── archive/
```

Semántica:

```text
inbox/
→ artifacts operativamente activos destinados a Coding Agents

outbox/
→ outputs pendientes de consumo o todavía requeridos por trabajo activo

archive/
→ cold storage operacional de artifacts retirados de circulación activa pero conservados por trazabilidad
```

```text
folder ≠ workflow state
archive ≠ aprobado
archive ≠ completado
archive ≠ memoria durable
archive ≠ repositorio de documentos vivos
```

Un documento vivo no usa `archive/` como repositorio por defecto.

## Manual Artifact Launcher

Es efímero y no autoritativo. Patrón preferido:

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

## Caveman Return

Cuando la Task declara:

```text
Output Delivery:
Channel: Exchange
Location: outbox
Filename: <TASK-ID>-REPORT.md
Caveman Return: Sí
```

y el output completo fue materializado correctamente, responde sólo:

```text
EJECUCIÓN: COMPLETADO
Atención requerida: Ninguna
Reporte: <PATH>
```

No repitas tests, commits, deploy, smoke ni detalle que ya vive en el Report.

Caveman Return es convención de entrega, no Artifact Type.

## Memoria durable y LLM Wiki

Memoria durable conserva conocimiento vigente y reusable. LLM Wiki es una posible materialización portable y navegable.

No uses Wiki como backlog, archivo de TASK/REPORT, log de chats o transcripciones. No obligues al coding agent a leerla completa.

## Actualizar la referencia local de IA-DOS

Instalación inicial y actualización son operaciones distintas.

Para una instalación existente:

```text
working tree limpio
→ verificar origin
→ git fetch origin
→ git switch main
→ comprobar divergencia
→ git pull --ff-only origin main
→ git rev-parse HEAD
→ git status
```

`git status` antes de `git fetch` NO demuestra que GitHub no tenga commits nuevos.

En Windows, cuando aplica la convención habitual:

```powershell
Set-Location (Join-Path $HOME "Proyectos\00-ia-dos")
```

No uses por rutina `git reset --hard`, `git clean`, merge/rebase implícitos o force push. Si existen cambios locales o divergencia, detente y revisa.

## Visualización opcional

Capacidades como Archify pueden evaluarse como visualización técnica opcional y Supporting Artifact. No son dependencia del core, fuente de verdad independiente ni Artifact Type.

## Regla final

```text
Conversation ≠ Task
Execution Cell ≠ Task
Authority Envelope ≠ Artifact Type
Execution Checkpoint ≠ autorización
Execution Report ≠ decisión
Exchange ≠ Google Drive
Exchange ≠ memoria
Specialist Handoff ≠ Exchange file
Manual Artifact Launcher ≠ autoridad
Caveman Return ≠ output completo

Task carries authority and the active delta.
Report carries evidence of what actually happened.
Durable memory carries current reusable knowledge.
Repository carries implementation.
Exchange only carries operational artifacts toward/from Coding Agents.
Human authority remains explicit.
```
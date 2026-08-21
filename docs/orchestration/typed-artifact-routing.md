# Tipado de artefactos y validación del receptor

Este contrato evita que un bloque destinado a un Conversation Space sea interpretado como una tarea para un coding agent, o viceversa.

## Regla principal

Todo bloque transferible nuevo comienza con:

```text
Artifact Type: [TIPO]
Destination Role: [ROL RECEPTOR]
Expected Output: [ARTEFACTO O REVISIÓN]
Forbidden Output: [ARTEFACTO O ACCIÓN]
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID O NO APLICA]
```

El receptor valida el encabezado antes de actuar.

## Contrato semántico único

Un mecanismo de transporte o almacenamiento no crea un tipo nuevo.

```text
Execution Task
= contrato de ejecución

Exchange
= pasarela pasiva de archivos Markdown
```

Una tarea transferida mediante Exchange sigue siendo la misma Execution Task. Exchange no genera, modifica, valida o coordina IDs, contratos, estados o permisos.

Una `Execution Cell` identifica continuidad de ejecución cuando el proyecto usa ese modelo, pero no reemplaza `Destination Role`, Cycle Owner ni autoridad por tarea.

`Manual Artifact Launcher`, `Output Delivery` y `Caveman Return` son convenciones de entrega. **No son Artifact Types** y no cambian el tipo ni la autoridad del artefacto.

## Identificadores

El Conversation Agent que construye una Execution Task asigna el `Task ID` antes del handoff o materialización como archivo.

Cuando el proyecto no usa otro esquema, IA-DOS recomienda:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

Ejemplo:

```text
PROYECTO-10-APP-20260821-130700
```

El timestamp usa orden `año-mes-día` seguido por `hora-minuto-segundo` para ordenar cronológicamente por texto y reducir colisiones en uso manual.

Una Execution Task candidata producida por Planning no recibe ese ID. Debe declarar:

```text
Task ID: PENDIENTE — ASIGNAR AL ADOPTAR
```

El Conversation Agent / Cycle Owner asigna la identidad sólo cuando adopta la candidata y construye la Execution Task real.

Si se materializa como Markdown, puede usarse:

```text
{TASK-ID}-TASK.md
{TASK-ID}-REPORT.md
```

El Execution Report reutiliza exactamente el Task ID de su Execution Task.

`Cycle ID` puede ser `NO APLICA`; no inventes un ciclo para satisfacer el encabezado.

El esquema temporal anterior es una recomendación para `Execution Task ID` cuando el proyecto no tiene otra convención. No convierte automáticamente los IDs de Planning u otros artefactos en timestamps obligatorios.

## Entrega manual opcional

Cuando un proyecto usa Exchange manual, el artefacto puede declarar una entrega semántica:

```text
Output Delivery:
Channel: Exchange
Location: outbox
Filename: [NOMBRE.md]
Caveman Return: Sí | No
```

Una instrucción efímera puede resolver `inbox/` y `outbox/` a paths absolutos mediante un `Manual Artifact Launcher`.

El launcher:

- localiza el artefacto;
- puede localizar físicamente el destino de output;
- puede repetir el modo de retorno ya declarado por la Task;
- no elige ni cambia ese modo;
- no modifica el artefacto;
- no agrega permisos;
- no reemplaza `Destination Role`, `Expected Output` ni `Forbidden Output`.

La conversación usa `Caveman Return` únicamente cuando la Task autoritativa declara `Caveman Return: Sí` **y** el output completo fue materializado correctamente. Si falta cualquiera de esas condiciones, el receptor devuelve el artefacto completo según el contrato y canal de la Task.

El artefacto completo continúa siendo la salida autoritativa.

Consulta `docs/execution/manual-artifact-delivery.md`.

## Tipos permitidos

### Specialist Handoff

```text
Artifact Type: Specialist Handoff
Destination Role: Conversation Space — [TÓPICO]
Expected Output: decisión de dominio | Planning Task | Environment Preflight | Execution Task
Forbidden Output: Implementation Plan | Execution Report | cambios técnicos
```

### Planning Task

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios del proyecto | commits | despliegues | Execution Report
```

La sesión de Planning, cuando se declara, puede ser un identificador lógico. No impone una política universal de conversación por tarea.

Si la Planning Task autoriza `Output Delivery`, el Code Agent puede materializar únicamente el Implementation Plan declarado sin dejar de ser solo lectura respecto del proyecto inspeccionado.

### Environment Preflight

```text
Artifact Type: Environment Preflight
Destination Role: Coding Agent — Planning
Expected Output: Environment Readiness Report
Forbidden Output: cambios del entorno | instalaciones | inicio de servicios | ejecución
```

La materialización explícitamente autorizada del Environment Readiness Report no cuenta como modificación del entorno inspeccionado.

### Environment Readiness Report

```text
Artifact Type: Environment Readiness Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión del readiness y decisión bajo la autoridad aplicable
Forbidden Output: iniciar ejecución automáticamente | modificar el entorno
```

Estados:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

Sólo `LISTO PARA EJECUCIÓN` permite considerar aprobación o reanudación de escritura.

### Implementation Plan

```text
Artifact Type: Implementation Plan
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión del plan bajo la autoridad aplicable
Forbidden Output: ejecución automática
```

El plan propone. No aprueba su propia Execution Task candidata ni asigna su Task ID.

### Execution Task

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar alcance | aprobar el propio resultado | iniciar otra unidad
```

Toda Execution Task mantiene explícitos:

- objetivo único;
- Cycle Owner y destino;
- Execution Cell o sesión cuando corresponda;
- alcance y fuera de alcance;
- autoridad y acceso;
- capacidades y acciones externas autorizadas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

El contexto durable puede compactarse, pero estos controles no desaparecen por compresión.

Si la tarea autoriza `Output Delivery`, materializar el Execution Report en el destino declarado no concede escritura adicional sobre el producto.

### Execution Resume

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: nueva Planning Task | replantear arquitectura | ampliar alcance | ampliar permisos
```

Conserva Task ID y sólo es válido cuando objetivo, alcance, autoridad, seguridad y arquitectura de la Execution Task original siguen sin cambios.

### Execution Report

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión de evidencia bajo la autoridad aplicable
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
```

Estados canónicos:

```text
COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
```

`Atención requerida` identifica un bloqueo, riesgo, desviación o decisión concreta que requiere revisión. No selecciona `APROBAR`, `CORREGIR`, `REVERTIR`, `ESCALAR` o `REVISAR MEMORIA`.

El Execution Report no crea por defecto una sección de conocimiento potencialmente durable ni una actualización recomendada.

## Autoridad después del retorno

`Destination Role: Cycle Owner` no significa autoridad humana ilimitada.

El Cycle Owner revisa y decide dentro de la autoridad delegada. La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

La evaluación de memoria durable ocurre después de revisar evidencia, salvo que una Execution Task haya autorizado una actualización documental concreta.

## Gate de compatibilidad

Antes de responder, valida:

1. ¿Mi rol coincide con `Destination Role`?
2. ¿El artefacto solicitado coincide con `Expected Output`?
3. ¿La acción requerida está autorizada?
4. ¿Existe contradicción entre encabezado y cuerpo?

Cuando el rol no coincida, no ejecutes. Ante contradicción prevalece la opción más restrictiva.

## Reglas por receptor

Un Conversation Space puede recibir Specialist Handoff, Environment Readiness Report, Implementation Plan o Execution Report.

Un coding agent puede recibir Planning Task, Environment Preflight, Execution Task o Execution Resume.

Ningún coding agent asume identidad de Conversation Space, Cycle Owner o Project Orchestrator ni decide el siguiente ciclo.

## Compatibilidad histórica

`Artifact: Implementation Plan` y `Artifact: Execution Report` pueden aparecer en artefactos históricos. Las salidas nuevas usan `Artifact Type:`.

## Cierre

El encabezado funciona como un tipo fuerte: declara quién puede actuar, qué salida se espera y qué está prohibido. El mecanismo usado para mover o conservar el artefacto no modifica ese contrato.
# Tipado de artefactos y validación del receptor

Este contrato evita que un bloque destinado a un Conversation Space sea interpretado como una tarea para un coding agent, o viceversa.

## Regla principal

Todo bloque transferible nuevo debe comenzar con:

```text
Artifact Type: [TIPO]
Destination Role: [ROL RECEPTOR]
Expected Output: [ARTEFACTO]
Forbidden Output: [ARTEFACTO O ACCIÓN]
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID O NO APLICA]
```

El receptor valida el encabezado antes de actuar.

## Contrato semántico único

IA-DOS mantiene un solo contrato semántico para cada tipo de artefacto.

Un mecanismo de transporte o almacenamiento no crea un tipo nuevo. En particular:

```text
Execution Task
    = contrato de ejecución

Exchange
    = pasarela pasiva de archivos Markdown
```

Por lo tanto, una tarea almacenada o transferida mediante Exchange sigue siendo exactamente la misma `Execution Task`, conserva `Destination Role: Coding Agent — Execution` y debe declarar alcance, autoridad, permisos, criterios, verificaciones y condiciones de detención suficientes para ejecutar con seguridad.

`Execution Cell` identifica continuidad de ejecución cuando el proyecto usa ese modelo, pero no reemplaza el rol receptor.

## Identificadores

El **Conversation Agent que construye la tarea** asigna el `Task ID` antes del handoff o de materializar el artefacto como archivo.

Exchange no genera, modifica, valida ni coordina IDs.

Cuando el proyecto no utiliza otro esquema acordado, IA-DOS recomienda para una `Execution Task` un identificador autocontenido:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

Ejemplo:

```text
PORTAL-10-APP-20260820-164500
```

Si el artefacto se materializa como Markdown, el Conversation Agent puede usar:

```text
PORTAL-10-APP-20260820-164500-TASK.md
```

El `Execution Report` reutiliza exactamente el mismo `Task ID` y, cuando se materializa como archivo:

```text
PORTAL-10-APP-20260820-164500-REPORT.md
```

Cuando no existe un `Cycle ID` separado, declara:

```text
Cycle ID: NO APLICA
```

No inventes un ciclo solamente para satisfacer el encabezado.

## Compatibilidad de transición

`Artifact: Implementation Plan` y `Artifact: Execution Report` siguen siendo alias heredados cuando el cuerpo conserva IDs, sesión o Execution Cell cuando corresponda, Cycle Owner y estado. Las salidas nuevas usan `Artifact Type:`.

## Tipos permitidos

### Specialist Handoff

```text
Artifact Type: Specialist Handoff
Destination Role: Conversation Space — [TÓPICO]
Expected Output: decisión de dominio | Planning Task | Execution Task
Forbidden Output: Implementation Plan | Execution Report | cambios técnicos
```

### Planning Task

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: cambios | commits | despliegues | Execution Report
```

### Environment Preflight

```text
Artifact Type: Environment Preflight
Destination Role: Coding Agent — Planning
Expected Output: Environment Readiness Report
Forbidden Output: cambios | instalaciones | inicio de servicios | ejecución
```

El preflight conserva el ciclo vigente cuando exista y solo comprueba precondiciones.

### Environment Readiness Report

```text
Artifact Type: Environment Readiness Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: Autorizar ejecución | Resolver dependencia | Corregir preflight | Escalar
Forbidden Output: iniciar ejecución automáticamente | modificar el entorno
```

El reporte declara `LISTO PARA EJECUCIÓN`, `NO LISTO` o `DESCONOCIDO` y no autoriza escritura por sí mismo.

### Implementation Plan

```text
Artifact Type: Implementation Plan
Destination Role: Cycle Owner — Conversation Space
Expected Output: Aprobar | Corregir | Rechazar | Escalar
Forbidden Output: ejecución automática
```

### Execution Task

```text
Artifact Type: Execution Task
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: ampliar alcance | aprobar el propio resultado | iniciar otra unidad
```

Toda Execution Task, independientemente de dónde se almacene o cómo se transporte, debe mantener explícitos los controles que no pueden inferirse de memoria conversacional:

- objetivo único;
- alcance incluido y fuera de alcance;
- autoridad y acceso de los recursos relevantes;
- capacidades o acciones externas autorizadas;
- criterios de aceptación;
- verificaciones esperadas;
- condiciones de detención;
- destino del Execution Report.

El contexto durable puede compactarse o referenciarse, pero estos controles operativos no deben desaparecer por compresión.

### Execution Resume

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: nueva Planning Task | replantear arquitectura | ampliar alcance
```

Conserva el `Task ID` y el `Cycle ID` cuando exista. Reanuda una tarea aprobada después de resolver una condición bloqueante.

### Execution Report

```text
Artifact Type: Execution Report
Destination Role: Cycle Owner — Conversation Space
Expected Output: revisión y decisión del Cycle Owner
Forbidden Output: aprobar el propio resultado | iniciar automáticamente el siguiente ciclo o tarea
```

El estado del reporte describe únicamente el resultado de la ejecución.

Estados canónicos:

```text
COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
```

Cuando exista un bloqueo, riesgo, desviación o decisión concreta que el Cycle Owner deba revisar, el reporte puede declararlo como `Atención requerida`. El coding agent no elige por adelantado la acción de gobierno posterior.

Después de revisar la evidencia, el Cycle Owner puede aprobar y cerrar, corregir, revertir, escalar o evaluar memoria durable. Estas son decisiones del receptor, no estados ni campos de decisión seleccionados por el executor.

## Gate de compatibilidad

Antes de responder, valida:

1. ¿Mi rol coincide con `Destination Role`?
2. ¿El artefacto solicitado coincide con `Expected Output`?
3. ¿La acción requerida está autorizada?
4. ¿Existe una contradicción entre encabezado y cuerpo?

Cuando el rol no coincida, no ejecutes: indica el rol esperado y devuelve el bloque sin transformarlo silenciosamente. Ante contradicción prevalece la opción más restrictiva.

## Reglas por receptor

Un Conversation Space puede recibir Specialist Handoff, Environment Readiness Report, Implementation Plan o Execution Report.

Un coding agent puede recibir Planning Task, Environment Preflight, Execution Task o Execution Resume.

Ningún coding agent asume identidad de Conversation Space, Cycle Owner o Project Orchestrator ni decide el siguiente ciclo.

## Cierre

El encabezado funciona como un tipo fuerte: declara quién puede actuar, qué puede producir y qué está prohibido. El mecanismo usado para mover o conservar el artefacto no modifica ese contrato.
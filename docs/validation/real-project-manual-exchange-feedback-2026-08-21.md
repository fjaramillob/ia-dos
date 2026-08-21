# Feedback de adopción real — Exchange manual — 2026-08-21

## Estado

```text
EVIDENCIA DE USO REAL
```

Este documento registra fricción observada al aplicar `v0.1.0-alpha.3` en un proyecto real después de la auditoría integral del repositorio.

No contiene paths personales, datos del producto ni detalles sensibles del proyecto adoptante.

## Escenario

El Conversation Agent produjo una `Planning Task` y el proyecto eligió materializarla como `.md` dentro de un Exchange local pasivo.

Flujo esperado conceptualmente:

```text
Conversation Agent
→ Planning Task.md
→ Exchange / inbox
→ Code Agent — Planning
→ Implementation Plan
→ Conversation Space / Cycle Owner
```

## Fricción 1 — faltaba un lanzamiento manual mínimo

Aunque la Planning Task estaba correctamente construida, la persona tuvo que indicar manualmente al Code Agent:

- que debía ejecutar una Planning Task;
- qué archivo físico debía leer;
- que ese archivo era el artefacto autoritativo.

La necesidad no pertenece a Exchange: Exchange sólo almacena archivos.

Aprendizaje:

```text
hace falta una instrucción efímera de localización
≠ hace falta un nuevo Artifact Type
```

Resultado de diseño: `Manual Artifact Launcher`.

## Fricción 2 — la respuesta conversacional duplicó el artefacto completo

El Code Agent devolvió un Implementation Plan largo directamente en la conversación.

El contenido técnico era útil como artefacto, pero la conversación no necesitaba repetir todo el detalle cuando el proyecto quería conservarlo como `.md` en `outbox/`.

Aprendizaje:

```text
artefacto completo
→ detalle, evidencia y trazabilidad

respuesta conversacional
→ estado, atención requerida y ubicación
```

Resultado de diseño: `Caveman Return` como representación conversacional mínima, no como artefacto nuevo.

## Fricción 3 — Planning read-only y escritura del propio output

Para dejar el Implementation Plan en `outbox/`, el Code Agent necesita crear un archivo.

La formulación previa “Planning es solo lectura / no modifica artefactos” podía interpretarse como prohibición absoluta de escribir incluso el propio output.

Se consolidó:

```text
Planning read-only
= no modifica proyecto ni fuentes inspeccionadas

Output Delivery autorizado
= puede materializar únicamente el artefacto de salida declarado
```

La misma frontera aplica a Environment Preflight.

## Fricción 4 — identidad de Execution Task poco visible

La convención recomendada ya existía:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

pero estaba principalmente en contratos de tipado y distribución offline, no suficientemente visible en la plantilla cotidiana de Execution Task.

Además, el Implementation Plan observado propuso una futura Execution Task con identidad ya asignada desde Planning.

Eso contradice el contrato vigente:

```text
Coding Agent — Planning
→ Task ID: PENDIENTE — ASIGNAR AL ADOPTAR

Conversation Agent / Cycle Owner
→ adopta la candidata
→ asigna Task ID
→ construye Execution Task real
```

La mejora vuelve visible el esquema temporal en plantillas completa/compacta de Execution Task sin convertirlo en una obligación universal para IDs de Planning.

## Solución adoptada

```text
TASK / PLAN .md
→ artefacto autoritativo completo

Manual Artifact Launcher
→ localización física efímera

Code Agent
→ trabajo dentro de autoridad

OUTPUT .md
→ artefacto completo en destino autorizado

Caveman Return
→ respuesta conversacional mínima
```

## Invariantes preservados

- Exchange continúa pasivo;
- launcher no es Artifact Type;
- Caveman Return no es Artifact Type;
- Output Delivery no amplía autoridad;
- Planning y Preflight siguen siendo de solo lectura respecto de sus fuentes;
- Execution Task sigue siendo el contrato de ejecución;
- Task ID sigue perteneciendo al Conversation Agent que construye la Execution Task real;
- no se agrega automatización, watcher, polling o trigger.

## Criterio de aprendizaje

La mejora se incorpora porque apareció en una ejecución real del método, no por completar una taxonomía abstracta.

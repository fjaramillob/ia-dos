# Propiedad y retorno del ciclo

Este documento define quién gobierna un resultado desde que se confirma hasta que se revisa su evidencia.

## Regla principal

El Conversation Space que confirma el resultado esperado se convierte en **Cycle Owner** mientras ese resultado permanezca dentro de su dominio.

`00 — Dirección y orquestación` también puede ser Cycle Owner cuando el resultado sea transversal, estratégico o no requiera especialización.

```text
orientar
→ confirmar resultado
→ asignar Cycle Owner
→ planificar o ejecutar
→ revisar el artefacto devuelto
→ cerrar, corregir o continuar
```

No existe un retorno automático a `00` entre definición, planificación y ejecución.

## Responsabilidades

El Cycle Owner debe:

- mantener el objetivo y los límites del ciclo;
- decidir si corresponde una Planning Task o una Execution Task;
- declarar las fuentes, artefactos y entornos autorizados;
- revisar el Implementation Plan cuando exista;
- aprobar una sola unidad ejecutable;
- revisar el Execution Report;
- decidir cierre, corrección o siguiente iteración;
- escalar solo cuando aparezca una decisión fuera de su autoridad.

## Destinos explícitos

Todo handoff técnico debe declarar por separado:

- **Cycle Owner**;
- **destino del Implementation Plan**;
- **destino del Execution Report**;
- **espacio de escalamiento**.

No uses un único campo `Retorno` cuando pueda confundirse planificación, ejecución y escalamiento.

## Cuándo escalar

Escala a `00` solo ante:

- cambio de objetivo o prioridad;
- conflicto entre dominios;
- expansión importante de alcance;
- decisión humana estratégica;
- nueva restricción no negociable;
- riesgo que el Cycle Owner no pueda resolver dentro de su autoridad.

Terminar una auditoría, producir un plan o recibir un reporte no son por sí solos razones para volver a `00`.

## Estado del resultado

El Cycle Owner debe identificar el estado vigente:

- `Propuesto`;
- `En validación`;
- `Aceptado`;
- `Bloqueado`;
- `Reemplazado`;
- `Descartado`;
- `Completado`.

Esto evita que propuestas, hallazgos y decisiones aceptadas se mezclen.

## Regla de cierre

Un ciclo termina cuando ocurre una de estas condiciones:

1. el resultado fue implementado y verificado;
2. existe una decisión humana específica pendiente;
3. el resultado fue reemplazado o descartado;
4. se activó un escalamiento justificado;
5. el siguiente resultado pertenece a un ciclo distinto y recibe un nuevo Cycle Owner.
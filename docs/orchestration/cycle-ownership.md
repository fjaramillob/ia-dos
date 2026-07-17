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
→ cerrar, corregir, transferir o continuar
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
- decidir cierre, corrección, transferencia o siguiente iteración;
- escalar solo cuando aparezca una decisión fuera de su autoridad que requiera dirección o coordinación transversal.

## Destinos explícitos

Todo handoff técnico debe declarar por separado:

- **Cycle Owner**;
- **destino del resultado de dominio**, cuando no sea un plan ni un reporte;
- **destino del Implementation Plan**;
- **destino del Execution Report**;
- **espacio de escalamiento**.

El destino normal de cada artefacto es el Cycle Owner que debe revisarlo. No uses un único campo `Retorno` cuando pueda confundirse planificación, ejecución, transferencia y escalamiento.

## Transferencia directa entre especialistas

Cuando el Cycle Owner descubre que el siguiente resultado pertenece claramente a otro dominio:

1. cierra o deja explícito el estado de su resultado actual;
2. prepara un handoff breve al Conversation Space correcto;
3. transfiere la propiedad del nuevo ciclo al destino cuando este confirme el resultado;
4. evita enviar el artefacto a `00` solo para que `00` repita el diagnóstico y lo vuelva a enrutar.

Ejemplo conceptual:

```text
20 confirma una brecha funcional
→ entrega handoff directo a 10
→ 10 asume identidad y Cycle Owner del nuevo resultado
```

Esto no es escalamiento. Es una transferencia de dominio.

## Identidad del espacio de destino

Todo handoff a otra conversación debe comenzar declarando literalmente:

```text
Esta conversación es [TÓPICO — NOMBRE DEL ESPACIO].
No reinicies el onboarding.
No reclasifiques el proyecto.
No te presentes como 00.
No repitas la configuración inicial de IA-DOS.
```

El espacio de destino debe responder desde ese rol y no reconstruir la fase inicial del proyecto.

## Cuándo escalar

Escala a `00` solo ante:

- cambio de objetivo o prioridad;
- conflicto entre dominios que requiera arbitraje;
- expansión importante de alcance;
- decisión humana estratégica;
- nueva restricción no negociable;
- riesgo que el Cycle Owner no pueda resolver dentro de su autoridad.

Terminar una auditoría, producir un plan, recibir un reporte o detectar una brecha clara de otro dominio no son por sí solos razones para volver a `00`.

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
5. el siguiente resultado pertenece a un ciclo distinto y recibe un nuevo Cycle Owner mediante transferencia directa.
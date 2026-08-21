# Salida rápida hacia planificación técnica

Este contrato evita cadenas innecesarias de conversaciones antes de llegar al entorno técnico real, sin saltarse memoria o readiness cuando son condiciones indispensables.

## Regla principal

El Conversation Space especialista gobierna el resultado. El coding agent inspecciona o ejecuta según el artefacto recibido.

```text
Conversation Space especialista
→ Memory Bootstrap Gate cuando aplica
→ Environment Preflight cuando readiness es desconocido
→ Execution Task directa si ya está lista
   o Planning Task si falta inspección/diseño
→ coding agent
→ artefacto vuelve al mismo Cycle Owner
```

Cuando `Memory Bootstrap Gate = BOOTSTRAP REQUIRED`, la ruta rápida no salta el bloqueo: emite únicamente una Execution Task separada para materializar el checkpoint mínimo y reevalúa la unidad original después de revisar ese reporte.

## Responsabilidades

### Conversation Space especialista / Cycle Owner

- confirma el resultado;
- mantiene objetivo y límites;
- evalúa memoria y readiness cuando corresponda;
- decide entre preflight, planificación y ejecución dentro de la autoridad delegada;
- prepara la tarea aplicable;
- revisa el retorno;
- solicita aprobación humana cuando la decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

### Coding agent

- usa `Coding Agent — Planning` en solo lectura cuando recibe `Planning Task` o `Environment Preflight`;
- devuelve `Implementation Plan` para Planning y `Environment Readiness Report` para Preflight;
- ejecuta únicamente cuando recibe una `Execution Task` autorizada;
- respeta las instrucciones y fuentes aplicables;
- produce evidencia verificable;
- no inicia otra unidad.

## Gate de salida rápida

Evalúa:

```text
1. ¿El resultado está suficientemente definido, es pequeño y verificable?
2. Si depende de historia, ¿la memoria necesaria ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿el coding agent puede proponer una primera unidad segura?
```

- **Memoria insuficiente:** aplica Memory Bootstrap Gate.
- **Readiness desconocido:** usa Environment Preflight.
- **Ejecución lista:** entrega Execution Task.
- **Falta inspección o diseño:** entrega Planning Task.
- **Decisión humana indispensable:** deriva sólo esa decisión.
- **Reorientación real:** escala a `00`.

La ruta rápida no significa omitir controles; significa no añadir conversaciones intermedias sin valor.

## Excepción de bootstrap

Si el gate devuelve `BOOTSTRAP REQUIRED`:

```text
unidad original
→ bloqueada

Execution Task de bootstrap
→ sólo checkpoint durable mínimo
→ unidad original fuera de alcance
→ Execution Report
→ revisión
→ reevaluar gate original
```

La tarea de bootstrap no declara `PASS` ni puede mezclar el resultado que busca desbloquear.

## Planning y Preflight

Los dos usan `Coding Agent — Planning` porque son de solo lectura, pero no son intercambiables:

```text
Planning Task
→ Coding Agent — Planning
→ Implementation Plan

Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

Sólo un readiness report con `LISTO PARA EJECUCIÓN` permite considerar autorización o reanudación de escritura; el reporte no concede esa autorización por sí mismo.

## Planning Task

Cuando corresponde planificación:

1. entrega una Planning Task autosuficiente;
2. indica que es de solo lectura;
3. declara el Cycle Owner y destino del Implementation Plan;
4. exige evidencia para hallazgos que condicionen la decisión;
5. pide una sola primera Execution Task candidata cuando exista evidencia suficiente.

No abras otro Conversation Space para que ese chat ejecute la Planning Task.

IA-DOS no impone una política universal sobre persistencia de conversaciones de planificación. Un identificador `PLAN — ...` no obliga a crear una conversación nueva por tarea.

## Frontera con Execution Cells

La autorización de Planning y Execution permanece separada, pero esto **no exige** abrir una conversación de ejecución nueva después de cada plan.

Si el proyecto ya tiene una Execution Cell adecuada y su conversación activa sigue respondiendo bien, la futura Execution Task puede reutilizarla. Los permisos vuelven a declararse en esa tarea.

## Evidencia mínima del Implementation Plan

Cada hallazgo relevante registra:

- recurso inspeccionado;
- ruta, referencia o identificador;
- estado observado;
- interpretación;
- límite de la evidencia.

Una afirmación sin evidencia identificable se marca como inferencia o propuesta.

## Límite del plan

El Implementation Plan debe cerrar una sola decisión técnica dominante y entregar:

- estado relevante comprobado;
- decisión recomendada;
- estrategia mínima;
- dependencias inmediatas;
- riesgos;
- una primera unidad ejecutable;
- Execution Task candidata cuando sea segura;
- una única razón bloqueante cuando no pueda prepararse.

No debe convertirse por defecto en arquitectura final o roadmap completo.

## Regla de cierre

La ruta rápida funciona cuando permite pasar directamente del Conversation Space al coding agent con el artefacto correcto, conservando Memory Bootstrap, readiness, autoridad, evidencia y revisión humana donde correspondan.

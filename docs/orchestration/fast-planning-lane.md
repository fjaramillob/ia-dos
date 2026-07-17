# Salida rápida hacia planificación técnica

Este contrato evita que IA-DOS convierta la planificación en una cadena de conversaciones antes de llegar al entorno técnico real.

## Regla principal

El Conversation Space especialista gobierna el resultado. El coding agent inspecciona el entorno y produce el plan técnico.

```text
Conversation Space especialista
→ Planning Task lista para copiar
→ coding agent inspecciona en solo lectura
→ Implementation Plan
→ vuelve al mismo especialista
→ especialista aprueba o corrige la primera Execution Task
→ coding agent ejecuta
→ Execution Report al especialista
```

## Responsabilidades distintas

### Conversation Space especialista

- confirma el resultado que debe planificarse;
- actúa como Cycle Owner;
- define objetivo, límites, fuentes y condiciones de detención;
- prepara la Planning Task;
- revisa el Implementation Plan;
- aprueba, corrige o rechaza la primera Execution Task candidata;
- revisa posteriormente el Execution Report.

### Coding agent

- inspecciona las fuentes y el entorno técnico real;
- respeta las instrucciones propias de los recursos autorizados;
- produce evidencia verificable;
- propone una estrategia mínima;
- entrega una primera Execution Task candidata;
- no escribe ni ejecuta durante la planificación.

## Regla de salida

Cuando ya existe suficiente dirección para que un coding agent inspeccione y proponga una primera unidad segura, el especialista debe terminar su respuesta con:

1. una instrucción visible que indique dónde pegar la tarea;
2. una Planning Task autosuficiente;
3. el destino exacto del Implementation Plan;
4. una acción verificable para el usuario.

No debe pedir abrir otro Conversation Space para que ese chat ejecute la Planning Task.

## Prohibición de autoejecución conversacional

Un Conversation Space no debe responder su propia Planning Task como si fuera el coding agent.

Solo puede hacerlo cuando se cumpla al menos una de estas condiciones:

- el usuario autoriza expresamente que ese mismo entorno realice la inspección técnica;
- no existe un coding agent disponible y el espacio tiene acceso técnico suficiente;
- la tarea no requiere inspección de artefactos o entorno técnico.

Cuando ocurra una excepción, debe declararse explícitamente:

```text
Este Conversation Space también actuará como agente de planificación técnica para esta tarea.
```

Sin esa declaración, una Planning Task siempre se dirige al coding agent.

## Umbral de acción

Antes de abrir otra conversación, pregunta:

```text
¿El coding agent disponible puede inspeccionar ahora
las fuentes autorizadas y producir un Implementation Plan seguro?
```

- **Sí:** entregar inmediatamente la Planning Task al coding agent.
- **No por falta de una decisión humana indispensable:** resolver o derivar solo esa decisión.
- **No por falta de acceso técnico:** declarar el bloqueo y el acceso requerido.
- **No por reorientación:** escalar a `00`.

Preguntas postergables, supuestos reversibles y alternativas técnicas no bloquean la salida.

## Evidencia mínima del Implementation Plan

Cada hallazgo que condicione la decisión debe incluir:

- recurso inspeccionado;
- ruta, referencia o identificador verificable;
- estado observado;
- interpretación y límite de la evidencia.

Una afirmación técnica sin evidencia identificable debe marcarse como inferencia o propuesta.

## Límite del plan

El Implementation Plan debe cerrar una sola decisión técnica dominante y entregar:

- estado relevante comprobado;
- decisión recomendada;
- estrategia mínima;
- primera unidad ejecutable;
- Execution Task candidata;
- dependencias inmediatas resumidas;
- una única razón bloqueante cuando no pueda preparar la tarea.

No debe diseñar detalladamente toda la iniciativa ni producir un roadmap completo por defecto.

## Regla de cierre

La planificación rápida funciona cuando el usuario puede pasar del especialista al coding agent con un solo bloque copiable y regresar al mismo especialista con un artefacto verificable para aprobación.
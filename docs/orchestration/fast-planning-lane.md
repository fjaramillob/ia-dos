# Salida rápida hacia planificación técnica

Este contrato evita que IA-DOS convierta la planificación en una cadena de conversaciones antes de llegar al entorno técnico real.

## Regla principal

El Conversation Space especialista gobierna el resultado. El coding agent inspecciona el entorno y produce el plan técnico.

```text
Conversation Space especialista
→ Execution Task directa cuando ya está lista
   o Planning Task cuando falta inspección
→ coding agent ejecuta o planifica
→ el artefacto vuelve al mismo especialista
```

## Responsabilidades distintas

### Conversation Space especialista

- confirma el resultado;
- actúa como Cycle Owner;
- decide entre ejecución directa y planificación técnica;
- define objetivo, límites, fuentes y condiciones de detención;
- prepara la Planning Task cuando falta inspección;
- revisa el Implementation Plan;
- aprueba, corrige o rechaza la primera Execution Task candidata;
- revisa posteriormente el Execution Report.

### Coding agent

- inspecciona las fuentes y el entorno técnico real cuando recibe una Planning Task;
- ejecuta únicamente cuando recibe una Execution Task aprobada;
- respeta las instrucciones propias de los recursos autorizados;
- produce evidencia verificable;
- no escribe ni ejecuta durante la planificación.

## Gate de salida rápida

Evalúa en este orden:

```text
1. ¿El resultado ya está suficientemente definido,
   es pequeño y puede ejecutarse con seguridad?
2. Si no, ¿el coding agent puede inspeccionar las fuentes
   y proponer una primera unidad segura?
```

- **Ejecución lista:** entrega una Execution Task directamente al coding agent.
- **Falta inspección o diseño:** entrega una Planning Task directamente al coding agent.
- **Falta una decisión humana indispensable:** resuelve o deriva solo esa decisión.
- **Falta acceso técnico:** declara el bloqueo y el acceso requerido.
- **Reorientación real:** escala a `00`.

La ruta rápida no obliga a planificar trabajo que ya está listo para ejecutar.

## Regla de salida de una Planning Task

Cuando corresponde planificación, el especialista debe terminar su respuesta con:

1. una instrucción visible que indique dónde pegar la tarea;
2. una Planning Task autosuficiente;
3. el destino exacto del Implementation Plan;
4. una acción verificable para el usuario.

No debe pedir abrir otro Conversation Space para que ese chat ejecute la Planning Task.

## Prohibición de autoejecución conversacional

Un Conversation Space no debe responder su propia Planning Task como si fuera el coding agent.

Solo puede hacerlo cuando se cumplan **todas** estas condiciones:

- el usuario autoriza expresamente que ese mismo entorno realice la inspección técnica;
- el espacio tiene acceso técnico suficiente a las fuentes y al entorno real;
- el espacio declara explícitamente:

```text
Este Conversation Space también actuará como agente de planificación técnica para esta tarea.
```

La ausencia de un coding agent no autoriza por sí sola la autoejecución. Sin las tres condiciones, la Planning Task debe dirigirse al coding agent o declararse bloqueada por falta de acceso.

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

La ruta rápida funciona cuando el usuario puede pasar directamente del especialista al coding agent con una Execution Task lista, o con una Planning Task que vuelve al mismo especialista como Implementation Plan verificable.

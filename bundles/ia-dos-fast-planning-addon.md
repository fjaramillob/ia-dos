# IA-DOS Fast Planning Addendum

Tipo: complemento del pack operativo para asistentes conversacionales sin acceso al repositorio canónico.

Complemento requerido: `ia-dos-agent-role-and-artifact-loop-addon.md`.

Ese complemento agrega el contrato de rol, `Cycle ID`, `Task ID`, `Agent Session` y encabezados de retorno al flujo offline.

## Propósito

Asegurar una salida rápida desde el Conversation Space especialista hacia Codex, Antigravity o el coding agent disponible.

## Regla central

```text
especialista gobierna
→ coding agent planifica
→ especialista revisa
→ coding agent ejecuta
```

El especialista actúa como Cycle Owner, define el objetivo, prepara la Planning Task y revisa el Implementation Plan. El coding agent inspecciona el entorno técnico real y produce el plan.

## No intermediación

No abras otro Conversation Space para que ese chat ejecute la Planning Task.

Cuando las fuentes permitan inspeccionar y proponer una primera unidad segura:

1. entrega una Planning Task autosuficiente;
2. indica exactamente dónde pegarla;
3. exige planificación de solo lectura;
4. devuelve el Implementation Plan al mismo especialista;
5. incluye una primera Execution Task candidata cuando exista evidencia suficiente.

## Excepción

Un Conversation Space solo puede actuar también como agente de planificación técnica cuando:

- el usuario lo autoriza expresamente;
- tiene acceso técnico suficiente;
- declara literalmente: `Este Conversation Space también actuará como agente de planificación técnica para esta tarea.`

## Evidencia

Cada hallazgo técnico que condicione la decisión debe incluir:

- recurso inspeccionado;
- ruta, referencia o identificador;
- estado observado;
- interpretación;
- límite de la evidencia.

Sin evidencia identificable, marca la afirmación como inferencia o propuesta.

## Planning Task mínima

Debe declarar:

- preparada por;
- ejecutada por;
- revisada por;
- Cycle Owner;
- destino del Implementation Plan;
- objetivo único;
- fuentes y autoridad;
- inspección mínima;
- fuera de alcance;
- condiciones de detención;
- formato del plan.

Aplica además los campos de rol, ciclo y sesión definidos en el complemento requerido.

## Implementation Plan mínimo

Debe incluir:

- estado comprobado relevante;
- evidencia verificable;
- decisión recomendada;
- estrategia mínima;
- decisiones pendientes clasificadas;
- primera unidad segura;
- Execution Task candidata lista para copiar;
- una única razón bloqueante cuando no pueda prepararse.

El encabezado de retorno debe conservar `Cycle ID` y `Agent Session`.

No debe convertirse por defecto en auditoría integral, arquitectura final y roadmap completo.

## Instrucción visible

> Abre Codex, Antigravity o el coding agent disponible sobre el entorno autorizado. Pega la Planning Task completa en modo de planificación de solo lectura. Devuelve el Implementation Plan a este mismo Conversation Space para revisión.

## Cierre

La planificación rápida es correcta cuando el usuario pasa del especialista al coding agent con un solo bloque copiable y vuelve al mismo especialista con evidencia suficiente para aprobar la primera ejecución.

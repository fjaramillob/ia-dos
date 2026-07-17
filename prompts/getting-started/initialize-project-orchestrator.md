# Inicializar el Project Orchestrator

Este recorrido configura IA-DOS dentro de un espacio conversacional persistente o entorno equivalente.

## Fuente canónica

```text
https://github.com/fjaramillob/ia-dos
```

El repositorio es la fuente canónica. Si la plataforma no puede navegarlo, usa el pack operativo y el addendum de planificación rápida disponibles.

## Configuración

1. Usa el nombre del proyecto como nombre del espacio.
2. Copia [Instrucciones persistentes](../../templates/project-instructions.template.md).
3. Carga una descripción breve y las fuentes disponibles.
4. Envía el primer mensaje siguiente.

## Primer mensaje

```text
Inicia este proyecto aplicando IA-DOS.

Proyecto: [NOMBRE DEL PROYECTO]

Descripción inicial:
[RESUMEN BREVE O REFERENCIA A UN ARCHIVO]

Fuentes disponibles:
- [REPOSITORIO, WIKI, DOCUMENTOS, SERVICIO, URL O NINGUNA]

Lee primero las fuentes y no repitas preguntas respondidas.
Clasifica el producto objetivo como nuevo o existente.

Primera respuesta:
1. Lo que entendí.
2. Prioridad propuesta.
3. Qué falta resolver ahora.
4. Organización de conversaciones.
5. Cómo trabajaremos.
6. Tu siguiente acción.

En “Organización de conversaciones”:
- usa `00 — Dirección y definición` para un producto nuevo o `00 — Descubrimiento y adopción` para uno existente;
- indica si por ahora basta trabajar en 00;
- menciona solo el próximo Conversation Space cuando aporte;
- no listes todos los espacios ni presentes una secuencia fija;
- aclara que se abren bajo demanda.

En “Cómo trabajaremos”, explica brevemente:
- 00 orienta la prioridad;
- el espacio que confirma el siguiente resultado se convierte en Cycle Owner;
- si el trabajo ya está definido, el especialista prepara una Execution Task directa;
- si falta inspección o diseño, el especialista prepara una Planning Task;
- Codex, Antigravity o el coding agent disponible inspecciona y produce el Implementation Plan;
- el plan vuelve al mismo especialista para revisión;
- una Execution Task aprobada produce un Execution Report que vuelve al mismo Cycle Owner;
- 00 recibe solo reorientaciones o escalamiento real.

“Tu siguiente acción” debe ser el último punto y pedir una acción verificable.
Mantén la respuesta breve. No entregues todavía un roadmap completo ni una auditoría extensa.

Cuando diga “avancemos”, “empecemos”, “ya tenemos suficiente” o equivalente:
- deja de repetir el diagnóstico;
- identifica el siguiente resultado verificable;
- asigna el Cycle Owner;
- aplica primero el gate de ejecución directa;
- si no corresponde ejecución directa, aplica el umbral de planificación;
- entrega una Execution Task o una Planning Task lista para copiar;
- no abras otro Conversation Space para que ese chat ejecute la Planning Task.

Gate de ejecución directa:
¿El siguiente resultado está suficientemente definido, es pequeño y puede ejecutarse con seguridad sin planificación técnica previa?
- Sí: prepara una Execution Task lista para pegar directamente en el coding agent disponible.
- No: evalúa si falta inspección o diseño técnico.

Umbral de planificación:
¿El coding agent disponible puede inspeccionar ahora las fuentes autorizadas y proponer una primera unidad segura?
- Sí: prepara una Planning Task lista para pegar directamente en Codex, Antigravity o el coding agent disponible.
- No porque falta una decisión humana indispensable: continúa o deriva solo esa decisión.
- No porque falta acceso técnico: declara el bloqueo y el acceso requerido.
- No porque requiere reorientación: escala a 00.

Una Planning Task:
- es de solo lectura;
- es preparada por el especialista;
- es ejecutada por el coding agent;
- produce un Implementation Plan;
- no autoriza escritura, commits, cambios remotos, despliegue, datos, recursos externos ni costes;
- vuelve al especialista Cycle Owner para revisión;
- debe pedir evidencia verificable de los hallazgos técnicos;
- debe incluir una primera Execution Task candidata cuando exista evidencia suficiente.

Un Conversation Space solo puede ejecutar su propia Planning Task cuando se cumplan todas estas condiciones:
- el usuario lo autoriza expresamente;
- tiene acceso técnico suficiente al entorno real;
- declara: `Este Conversation Space también actuará como agente de planificación técnica para esta tarea.`

Antes de aprobar una Execution Task aplica el gate de tamaño:
¿Puede completarse, verificarse y reportarse como una sola unidad sin mezclar resultados independientes?
Si no, divide el plan y aprueba solo la primera unidad.

Todo handoff técnico debe declarar por separado:
- quién prepara la tarea;
- quién la ejecuta;
- Cycle Owner;
- destino del Implementation Plan;
- destino del Execution Report;
- espacio de escalamiento;
- estado del resultado.

Antes de enviar trabajo al coding agent, identifica los recursos reales y declara para cada uno:
- rol;
- autoridad para qué ámbito;
- acceso permitido;
- limitaciones.

No impongas carpetas, repositorios separados, una Wiki independiente, GitHub, trabajo local, proveedor, agente o stack concreto.

No menciones nombres, rutas, dominios o repositorios de otros proyectos salvo que sean fuentes explícitas del proyecto actual.
```

## Transición esperada a planificación

Cuando corresponda una Planning Task, la respuesta debe incluir una instrucción visible:

> Abre Codex, Antigravity o el coding agent disponible sobre el entorno técnico autorizado. Inicia una sesión de planificación en solo lectura, pega la Planning Task completa y devuelve el `Implementation Plan` al mismo Conversation Space especialista. No ejecutes cambios.

El especialista no debe pedir abrir otro chat para producir el plan.

## Transición esperada a ejecución

Cuando corresponda una Execution Task, la respuesta debe incluir una instrucción visible:

> Abre el coding agent disponible sobre el entorno autorizado e inicia una sesión de ejecución. Pega la Execution Task completa. No amplíes el alcance. Devuelve el `Execution Report` al Cycle Owner indicado.

El bloque entregado debe poder copiarse sin reconstruir contexto desde mensajes anteriores.

Consulta:

- [Avance concreto y transición a coding agents](../../docs/orchestration/concrete-execution-flow.md);
- [Salida rápida hacia planificación técnica](../../docs/orchestration/fast-planning-lane.md).

## Resultado esperado

El onboarding está bien encaminado cuando:

- comprende el alma y la prioridad;
- identifica `00` y orienta la organización mínima;
- abre solo el espacio que desbloquea trabajo;
- asigna propiedad explícita del ciclo;
- preserva ejecución directa cuando el trabajo ya está listo;
- distingue gobierno conversacional de inspección técnica;
- entrega la Planning Task directamente al coding agent cuando hace falta planificar;
- evita tareas y planes demasiado grandes;
- exige evidencia verificable;
- no presupone estructura física ni herramientas;
- devuelve planes y reportes al especialista responsable;
- reserva `00` para dirección y escalamiento;
- conserva lenguaje y referencias agnósticas.

# Inicializar el Project Orchestrator

Este recorrido configura IA-DOS dentro de un espacio conversacional persistente o entorno equivalente.

## Fuente canónica

```text
https://github.com/fjaramillob/ia-dos
```

El repositorio es la fuente canónica. Si la plataforma no puede navegarlo, usa como contrato offline mínimo `ORCHESTRATOR.md` junto con `templates/project-instructions.template.md`. No combines bundles o addenda heredados para construir un onboarding nuevo.

`bundles/ia-dos-current-offline-pack.md` puede utilizarse sólo cuando su propio encabezado declare que está sincronizado con la versión o commit de IA-DOS adoptado.

## Configuración

1. Usa el nombre del proyecto como nombre del espacio principal.
2. Copia [Instrucciones persistentes](../../templates/project-instructions.template.md) cuando la plataforma permita instrucciones estables.
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
- usa `00 — Dirección y orquestación` como Conversation Space inicial canónico;
- para un producto nuevo trabaja en modo `definición inicial`;
- para un producto existente trabaja en modo `descubrimiento y adopción`;
- indica si por ahora basta trabajar en 00;
- consulta `docs/orchestration/topic-routing-registry.md` como única lista normativa de Conversation Spaces;
- menciona solo el próximo Conversation Space cuando una brecha dominante requiera contexto persistente propio;
- no listes todos los espacios ni presentes una secuencia fija;
- aclara que se abren bajo demanda.

En “Cómo trabajaremos”, explica brevemente:
- 00 orienta la prioridad y recibe reorientaciones o escalamiento real;
- el espacio que confirma el siguiente resultado se convierte en Cycle Owner;
- si el trabajo ya está definido, prepara una Execution Task directa;
- si falta inspección o diseño, prepara una Planning Task de solo lectura;
- el coding agent produce el Implementation Plan o ejecuta la Execution Task según el rol recibido;
- cada resultado vuelve al mismo Cycle Owner para revisión;
- una conversación del coding agent no equivale a una tarea: cuando el proyecto use Execution Cells, las tareas de ejecución reutilizan la célula adecuada mientras siga respondiendo bien;
- permisos y alcance se vuelven a declarar en cada Execution Task.

“Tu siguiente acción” debe ser el último punto y pedir una acción verificable.
Mantén la respuesta breve. No entregues todavía un roadmap completo ni una auditoría extensa.

Cuando diga “avancemos”, “empecemos”, “ya tenemos suficiente” o equivalente:
- deja de repetir el diagnóstico;
- identifica el siguiente resultado verificable;
- asigna el Cycle Owner;
- aplica primero el gate de ejecución directa;
- si no corresponde ejecución directa, aplica el umbral de planificación;
- entrega una Execution Task o una Planning Task lista para copiar;
- no abras otro Conversation Space solo para que ese chat ejecute la Planning Task.

Gate de ejecución directa:
¿El siguiente resultado está suficientemente definido, es pequeño y puede ejecutarse con seguridad sin planificación técnica previa?
- Sí: prepara una Execution Task lista para el coding agent disponible.
- No: evalúa si falta inspección o diseño técnico.

Umbral de planificación:
¿El coding agent disponible puede inspeccionar ahora las fuentes autorizadas y proponer una primera unidad segura?
- Sí: prepara una Planning Task de solo lectura.
- No porque falta una decisión humana indispensable: continúa o deriva solo esa decisión.
- No porque falta acceso técnico: declara el bloqueo y el acceso requerido.
- No porque requiere reorientación: escala a 00.

Una Planning Task:
- es preparada por el Conversation Space que gobierna el resultado;
- es ejecutada por `Coding Agent — Planning`;
- es de solo lectura;
- produce un Implementation Plan;
- no autoriza escritura, commits, cambios remotos, despliegue, datos, recursos externos ni costes;
- vuelve al Cycle Owner para revisión;
- debe pedir evidencia verificable de los hallazgos técnicos;
- debe incluir una primera Execution Task candidata cuando exista evidencia suficiente.

La política de persistencia o renovación de conversaciones de planificación no forma parte del onboarding v0 y no debe inventarse por analogía con Execution Cells.

Un Conversation Space solo puede ejecutar su propia Planning Task cuando se cumplan todas estas condiciones:
- el usuario lo autoriza expresamente;
- tiene acceso técnico suficiente al entorno real;
- declara: `Este Conversation Space también actuará como agente de planificación técnica para esta tarea.`

Antes de aprobar una Execution Task aplica el gate de tamaño:
¿Puede completarse, verificarse y reportarse como una sola unidad sin mezclar resultados independientes?
Si no, divide el plan y aprueba solo la primera unidad.

Toda Execution Task debe seguir el contrato canónico de `docs/orchestration/typed-artifact-routing.md`. Exchange Protocol v0 puede cambiar su identificación y persistencia, pero no crea un contrato de ejecución distinto.

Antes de enviar trabajo al coding agent, identifica los recursos reales y declara para cada uno:
- rol;
- autoridad para qué ámbito;
- acceso permitido;
- limitaciones.

No impongas carpetas, repositorios separados, una Wiki independiente, Exchange, GitHub, trabajo local, proveedor, agente o stack concreto.

No menciones nombres, rutas, dominios o repositorios de otros proyectos salvo que sean fuentes explícitas del proyecto actual.
```

## Transición esperada a planificación

Cuando corresponda una Planning Task, la respuesta debe incluir una instrucción visible equivalente a:

> Abre el coding agent disponible sobre el entorno técnico autorizado. Ejecuta la Planning Task en modo de solo lectura y devuelve el `Implementation Plan` al mismo Conversation Space Cycle Owner. No ejecutes cambios.

No conviertas el nombre o cantidad de conversaciones de planificación en una regla del método mientras esa política permanezca abierta.

## Transición esperada a ejecución

Cuando corresponda una Execution Task, la respuesta debe incluir una instrucción visible equivalente a:

> Abre la Execution Cell adecuada del coding agent o el entorno de ejecución disponible. Pega la Execution Task completa. No amplíes el alcance. Devuelve el `Execution Report` al Cycle Owner indicado.

Si ya existe una conversación activa para esa Execution Cell y continúa respondiendo correctamente, reutilízala. No abras una conversación nueva por cada tarea.

El bloque entregado debe poder ejecutarse sin reconstruir la historia desde mensajes anteriores.

Consulta:

- [Registro de tópicos](../../docs/orchestration/topic-routing-registry.md);
- [Avance concreto y transición a coding agents](../../docs/orchestration/concrete-execution-flow.md);
- [Salida rápida hacia planificación técnica](../../docs/orchestration/fast-planning-lane.md);
- [Execution Cells y Exchange Protocol v0](../../docs/execution/execution-cells-and-exchange.md).

## Resultado esperado

El onboarding está bien encaminado cuando:

- comprende propósito y prioridad suficientes para avanzar;
- identifica `00 — Dirección y orquestación` y el modo de entrada correcto;
- usa el registro canónico para enrutar conversaciones;
- abre solo el espacio que desbloquea trabajo;
- asigna propiedad explícita del ciclo;
- preserva ejecución directa cuando el trabajo ya está listo;
- distingue gobierno conversacional de planificación y ejecución técnica;
- no crea una conversación de coding agent por cada Execution Task;
- evita tareas y planes demasiado grandes;
- exige evidencia verificable;
- no presupone estructura física ni herramientas;
- devuelve planes y reportes al Cycle Owner;
- conserva lenguaje y referencias agnósticas.

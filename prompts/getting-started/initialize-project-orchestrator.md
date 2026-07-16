# Inicializar el Project Orchestrator

Este recorrido configura IA-DOS dentro de un espacio conversacional persistente o entorno equivalente.

## Fuente canónica

```text
https://github.com/fjaramillob/ia-dos
```

El repositorio es la fuente canónica. Si la plataforma no puede navegarlo, usa el pack operativo disponible.

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
- el Cycle Owner decide si corresponde planificación técnica o ejecución directa;
- un Implementation Plan vuelve al destino declarado para revisión;
- una Execution Task aprobada produce un Execution Report que vuelve al destino declarado;
- 00 recibe solo reorientaciones o escalamiento real.

“Tu siguiente acción” debe ser el último punto y pedir una acción verificable.
Mantén la respuesta breve. No entregues todavía un roadmap completo ni una auditoría extensa.

Cuando diga “avancemos”, “empecemos”, “ya tenemos suficiente” o equivalente:
- deja de repetir el diagnóstico;
- identifica el siguiente resultado verificable;
- abre como máximo un Conversation Space cuando exista una brecha real;
- asigna el Cycle Owner;
- aplica el gate de planificación.

Gate de planificación:
¿El siguiente resultado está suficientemente definido, es pequeño y puede ejecutarse con seguridad sin planificación técnica previa?
- Sí: prepara una Execution Task.
- No porque falta inspección o diseño técnico: prepara una Planning Task.
- No porque falta una decisión de dominio: continúa o deriva al Conversation Space correspondiente.
- No porque requiere reorientación: escala a 00.

Una Planning Task:
- es de solo lectura;
- produce un Implementation Plan;
- no autoriza escritura, commits, cambios remotos, despliegue, datos, recursos externos ni costes;
- vuelve al destino de revisión declarado.

Antes de aprobar una Execution Task aplica el gate de tamaño:
¿Puede completarse, verificarse y reportarse como una sola unidad sin mezclar resultados independientes?
Si no, divide el plan y aprueba solo la primera unidad.

Todo handoff técnico debe declarar por separado:
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

> Abre el entorno disponible para el proyecto e inicia una sesión de planificación en solo lectura. Pega la Planning Task siguiente. Devuelve el `Implementation Plan` completo al Conversation Space indicado y no ejecutes cambios.

## Transición esperada a ejecución

Cuando corresponda una Execution Task, la respuesta debe incluir una instrucción visible:

> Abre el entorno disponible para el proyecto e inicia una sesión de ejecución. Pega la Execution Task siguiente. No amplíes el alcance. Devuelve el `Execution Report` completo al Conversation Space indicado.

El bloque entregado debe poder copiarse sin reconstruir contexto desde mensajes anteriores.

Consulta [Avance concreto y transición a coding agents](../../docs/orchestration/concrete-execution-flow.md).

## Resultado esperado

El onboarding está bien encaminado cuando:

- comprende el alma y la prioridad;
- identifica `00` y orienta la organización mínima;
- abre solo el espacio que desbloquea trabajo;
- asigna propiedad explícita del ciclo;
- distingue planificación de ejecución;
- evita tareas demasiado grandes;
- no presupone estructura física ni herramientas;
- devuelve planes y reportes a destinos explícitos;
- reserva `00` para dirección y escalamiento;
- conserva lenguaje y referencias agnósticas.
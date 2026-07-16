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
3. Carga el pack, una descripción breve y las fuentes disponibles.
4. Envía el primer mensaje siguiente.

## Primer mensaje

```text
Inicia este proyecto aplicando IA-DOS.

Proyecto: [NOMBRE DEL PROYECTO]

Descripción inicial:
[RESUMEN BREVE O REFERENCIA A UN ARCHIVO]

Fuentes disponibles:
- [REPOSITORIO, WIKI, DOCUMENTOS, URL O NINGUNA]

Lee primero las fuentes y no repitas preguntas respondidas.
Clasifica el producto objetivo como nuevo o existente.

Primera respuesta:
1. Lo que entendí.
2. Prioridad propuesta.
3. Qué falta resolver ahora.
4. Cómo trabajaremos: explica brevemente el ciclo entre esta conversación y el entorno de ejecución.
5. Tu siguiente acción: termina siempre con una acción concreta que yo deba realizar.

En “Cómo trabajaremos”, explica de forma precisa y adaptada al proyecto:
- aquí aclararemos solo lo indispensable;
- cuando exista suficiente definición, me entregarás instrucciones listas para el coding agent disponible;
- el coding agent modificará el producto y la Wiki cuando corresponda;
- traeré de vuelta el Execution Report;
- revisaremos el resultado aquí y volveremos a iterar.

No presentes esta explicación como un roadmap ni describas todos los Conversation Spaces.

“Tu siguiente acción” debe ser el último punto y pedir una acción verificable. Por ejemplo:
- responder una pregunta pendiente;
- corregir una interpretación;
- confirmar la dirección escribiendo “ok”;
- decir “avancemos” para preparar el siguiente handoff o Execution Task.

No cierres con una explicación pasiva o con “cuando quieras”.

Mantén la respuesta breve. No entregues todavía un roadmap completo, una auditoría extensa ni todos los Conversation Spaces posibles.

Cuando diga “avancemos”, “empecemos”, “ya tenemos suficiente” o equivalente:
- deja de repetir el diagnóstico;
- identifica el siguiente resultado verificable;
- evalúa si ya existe suficiente claridad para preparar una Execution Task.

Si ya existe suficiente claridad:
- entrega un prompt listo para el coding agent disponible;
- indica exactamente en qué proyecto, repositorio o entorno debe pegarse;
- pide que el Execution Report vuelva al espacio que originó la tarea.

Si falta definición:
- abre solo el Conversation Space que resuelve la brecha principal;
- entrega un handoff breve y autosuficiente.

No abras 10, 20, 30 y 90 como una secuencia automática.

Usa Conversation Spaces bajo demanda:
- 10 — Producto y UX: comportamiento o experiencia;
- 20 — Arquitectura y stack: decisión arquitectónica o lectura de una auditoría;
- 30 — Ejecución y desarrollo: preparación de tareas complejas, solo si aporta;
- 90 — Wiki y memoria: síntesis o mantenimiento durable complejo.

Cada espacio debe cerrar con una sola salida útil:
- prompt para otra conversación;
- prompt listo para coding agent;
- Wiki Update Task o insumos;
- una decisión humana pendiente.

No menciones nombres, rutas, dominios o repositorios de otros proyectos. Usa solo los parámetros y fuentes entregados para el proyecto actual.
```

## Transición esperada a ejecución

Cuando una tarea esté suficientemente definida, la respuesta debe incluir una instrucción visible:

> Ahora abre el proyecto correspondiente en el entorno de ejecución disponible, inicia una nueva sesión y pega el prompt siguiente. Cuando termine, trae aquí el `Execution Report` completo para revisarlo antes de continuar.

El bloque entregado debe poder copiarse sin reconstruir contexto desde mensajes anteriores.

Consulta [Avance concreto y transición a coding agents](../../docs/orchestration/concrete-execution-flow.md).

## Resultado esperado

El onboarding está bien encaminado cuando el asistente:

- comprende el alma y la prioridad;
- explica con precisión el ciclo conversación → coding agent → Execution Report → iteración;
- termina con una acción concreta para el usuario;
- evita expansión innecesaria;
- abre solo el espacio que desbloquea trabajo;
- entrega pronto una tarea ejecutable;
- recibe evidencia del coding agent;
- decide el siguiente ciclo desde el espacio que originó la tarea o vuelve a `00` solo para reorientar;
- conserva lenguaje y referencias agnósticas.
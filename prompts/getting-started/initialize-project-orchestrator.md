# Inicializar el Project Orchestrator

Este recorrido configura IA-DOS dentro de un Project de ChatGPT, Gem de Gemini, Project de Claude o entorno equivalente.

## Repositorio oficial

```text
https://github.com/fjaramillob/ia-dos
```

El repositorio es la fuente canónica. Si la plataforma no puede navegar GitHub, usa `ia-dos-project-orchestrator-pack.md` como fuente operativa.

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
4. Tu siguiente acción.
5. Cómo trabajaremos: explica en pocas líneas el recorrido esperado para que el usuario sepa qué viene después.

La explicación del recorrido debe ser breve y adaptada al proyecto. Debe comunicar, sin presentar un roadmap completo, que normalmente:
- primero se aclara solo la definición indispensable;
- si hace falta, se abre un único Conversation Space para resolver la brecha principal;
- cuando exista claridad suficiente, se entrega un prompt listo para Codex, Antigravity, Claude Code u otro coding agent;
- el coding agent modifica el producto y la Wiki cuando corresponda;
- el Execution Report vuelve al espacio que originó la tarea para revisión;
- 00 interviene nuevamente solo si aparece una reorientación, conflicto o decisión estratégica.

Mantén la respuesta breve. No entregues todavía un roadmap completo, una auditoría extensa ni todos los Conversation Spaces posibles.

Cuando diga “avancemos”, “empecemos”, “ya tenemos suficiente” o equivalente:
- deja de repetir el diagnóstico;
- identifica el siguiente resultado verificable;
- evalúa si ya existe suficiente claridad para preparar una Execution Task.

Si ya existe suficiente claridad:
- entrega un prompt listo para Codex, Antigravity, Claude Code u otro coding agent;
- indica exactamente en qué proyecto o repositorio debe pegarse;
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
```

## Transición esperada a ejecución

Cuando una tarea esté suficientemente definida, la respuesta debe incluir una instrucción visible:

> Ahora abre el proyecto correspondiente en Codex o Antigravity, inicia una nueva conversación y pega el prompt siguiente. Cuando termine, trae aquí el `Execution Report` completo para revisarlo antes de continuar.

El bloque entregado debe poder copiarse sin reconstruir contexto desde mensajes anteriores.

Consulta [Avance concreto y transición a coding agents](../../docs/orchestration/concrete-execution-flow.md).

## Resultado esperado

El onboarding está bien encaminado cuando el asistente:

- comprende el alma y la prioridad;
- explica brevemente al usuario cómo se avanzará desde definición hacia ejecución;
- evita expansión innecesaria;
- abre solo el espacio que desbloquea trabajo;
- entrega pronto una tarea ejecutable;
- recibe evidencia del coding agent;
- decide el siguiente ciclo desde el espacio que originó la tarea o vuelve a `00` solo para reorientar.

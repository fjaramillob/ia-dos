# Avance concreto y transición a coding agents

IA-DOS debe producir avances verificables, no expandir indefinidamente el análisis entre conversaciones.

## Flujo principal

```text
capturar alma y prioridad
→ identificar el siguiente resultado concreto
→ resolver solo la definición indispensable
→ preparar una Execution Task
→ entregar un prompt listo para el coding agent
→ ejecutar
→ recibir un Execution Report
→ revisar en 00
→ decidir el siguiente ciclo
```

La conversación se expande por especialización solo cuando esa especialización desbloquea trabajo. No debe acumular toda la definición dentro de `00` ni abrir todos los espacios por anticipación.

## Gate antes de abrir otra conversación

El Project Orchestrator debe evaluar:

```text
¿Existe suficiente claridad para preparar una tarea acotada, verificable y segura?
```

### Cuando la respuesta es sí

No abras otra conversación por rutina. Entrega inmediatamente:

1. una instrucción visible para abrir el proyecto correcto en Codex, Antigravity, Claude Code u otro coding agent;
2. un prompt autosuficiente listo para copiar;
3. la indicación de traer de vuelta el `Execution Report` completo.

### Cuando la respuesta es no

Identifica la brecha principal y abre solo el espacio que la resuelve:

- `10 — Producto y UX`: comportamiento, flujo, usuario o experiencia;
- `20 — Arquitectura y stack`: límites técnicos, alternativas o decisión arquitectónica;
- `30 — Ejecución y desarrollo`: preparación de una tarea compleja que no puede producirse con claridad desde el espacio actual;
- `90 — Wiki y memoria`: síntesis, contradicciones o mantenimiento durable complejo.

`30` no es un paso obligatorio. Cualquier espacio puede producir una `Execution Task` cuando dispone de suficiente definición.

## Formato de transición visible

Usa una instrucción equivalente a:

> Ahora abre el proyecto `[PROYECTO O REPOSITORIO]` en Codex o Antigravity, inicia una nueva conversación y pega el prompt siguiente. No amplíes el alcance. Cuando termine, trae aquí el `Execution Report` completo para revisarlo antes de continuar.

Después incluye un único bloque listo para copiar. El usuario no debe reconstruir la tarea combinando varios mensajes o handoffs.

## Contenido mínimo del prompt ejecutable

```text
Rol y repositorio
Objetivo
Estado o problema observado
Fuentes y contexto mínimo
Alcance
Fuera de alcance
Rutas autorizadas y prohibidas
Capacidades requeridas
Criterios de aceptación
Pruebas o verificaciones
Condiciones de detención
Reglas de Git y pull request
Formato del Execution Report
```

Declara de forma explícita si la tarea es:

- solo lectura;
- modificación local sin commit;
- branch y commits autorizados;
- apertura de pull request autorizada;
- merge no autorizado salvo confirmación posterior.

## Regreso al Project Orchestrator

Cuando el coding agent finalice, el usuario devuelve su respuesta al espacio que originó la tarea, normalmente `00`.

La revisión debe responder únicamente:

1. ¿se cumplió el objetivo?;
2. ¿los criterios tienen evidencia?;
3. ¿el diff respetó el alcance?;
4. ¿qué quedó bloqueado o parcial?;
5. ¿qué decisión o tarea sigue?;
6. ¿qué aprendizaje debe registrarse en la wiki?

No repitas la auditoría completa si el reporte ya contiene evidencia suficiente.

## Salida obligatoria de los Conversation Spaces

Cada espacio debe detener su expansión cuando pueda entregar una de estas salidas:

1. prompt para otro Conversation Space;
2. prompt listo para coding agent;
3. `Wiki Update Task` o insumos para ella;
4. una única decisión humana pendiente.

Un documento largo no es mejor por ser largo. El entregable debe contener solo lo necesario para desbloquear la siguiente acción.

## Ejemplo mínimo

```text
Lo suficiente ya está definido para revisar la implementación.

Ahora abre el proyecto en Codex o Antigravity y pega el prompt siguiente.
Cuando termine, trae aquí el Execution Report completo.

[PROMPT EJECUTABLE]
```

## Guardrails

- no enviar al coding agent una intención vaga como “mejora lo necesario”;
- no entregar toda la wiki cuando basta un Context Pack;
- no pedir ejecución física a un Conversation Space;
- no asumir acceso, permisos o herramientas;
- no convertir una estrategia aprobada en autorización de escritura;
- no abrir otra conversación para posponer una tarea que ya puede ejecutarse;
- no declarar completado algo sin diff, pruebas o evidencia aplicable.

## Regla principal

```text
La expansión ocurre entre conversaciones especializadas.
El avance ocurre mediante tareas concretas y evidencia.
```

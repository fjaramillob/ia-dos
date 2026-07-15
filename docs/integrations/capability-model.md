# Modelo de capacidades

IA-DOS debe decidir y ejecutar según capacidades reales, no según supuestos sobre ChatGPT, Gemini, Claude, Codex, Antigravity, Claude Code u otra plataforma.

## Objetivo

El modelo de capacidades permite responder cuatro preguntas antes de actuar:

1. ¿Qué necesita la tarea?
2. ¿Qué puede hacer realmente esta sesión o herramienta?
3. ¿Qué está autorizado?
4. ¿Qué evidencia puede devolver?

## Capacidad, permiso y autorización

Mantén separadas estas capas:

```text
Capacidad
La herramienta puede realizar una operación.

Permiso
La identidad conectada tiene acceso técnico suficiente.

Autorización
La persona responsable aprobó esa operación para esta tarea.

Ejecución
La herramienta realizó la acción.

Verificación
Existe evidencia del resultado.
```

Ninguna capa implica automáticamente la siguiente.

## Dominios de capacidad

Registra únicamente los dominios relevantes para el proyecto:

- conversación y razonamiento;
- búsqueda web o investigación;
- archivos adjuntos;
- LLM Wiki;
- repositorios Git;
- issues y pull requests;
- filesystem local;
- terminal o CLI;
- ejecución de código y pruebas;
- CI/CD;
- despliegue y producción;
- bases de datos;
- almacenamiento;
- documentación y suites ofimáticas;
- correo, calendario o mensajería;
- observabilidad y logs;
- servicios externos mediante API, conector o MCP.

## Operaciones

Para cada dominio, distingue operaciones concretas:

```text
none
read
search
create
update
delete
execute
admin
```

No uses etiquetas amplias como “acceso completo” cuando puedes declarar operaciones específicas.

## Estados de una capacidad

Una capacidad puede estar:

- `verified`: comprobada en la sesión actual;
- `declared`: informada por la plataforma, pero no utilizada aún;
- `unavailable`: no existe o no está conectada;
- `unknown`: no se ha verificado;
- `blocked`: existe, pero falta permiso o autorización;
- `degraded`: disponible parcialmente o mediante un flujo alternativo.

## Verificación mínima

Una capacidad se considera `verified` cuando existe evidencia suficiente, por ejemplo:

- la herramienta aparece en la sesión;
- una operación de lectura confirma el recurso correcto;
- la cuenta, workspace, proyecto o repositorio fue identificado;
- el resultado devuelve un identificador verificable;
- una prueba no destructiva confirma el alcance.

No realices una escritura solo para comprobar que la escritura funciona. Usa metadata, permisos declarados o una acción segura y reversible cuando corresponda.

## Selección de herramienta

El Project Orchestrator debe elegir la herramienta más adecuada según:

- capacidad requerida;
- acceso disponible;
- sensibilidad de la fuente;
- reversibilidad;
- trazabilidad;
- evidencia disponible;
- riesgo y coste;
- fricción para la persona responsable.

Preferencias generales:

```text
lectura antes que escritura
operación específica antes que acceso amplio
cambio reversible antes que irreversible
evidencia directa antes que afirmación del modelo
herramienta especializada antes que simulación conversacional
```

## Capability Manifest

Un proyecto puede mantener un `Capability Manifest` cuando utiliza varias plataformas, conectores o agentes y necesita recordar sus límites operativos.

El manifest debe registrar:

- herramienta o plataforma;
- dominio;
- operaciones disponibles;
- estado de verificación;
- identidad o contexto conectado sin exponer secretos;
- alcance permitido;
- restricciones;
- acciones que requieren aprobación;
- evidencia o fecha de última verificación.

No debe contener credenciales, tokens ni datos sensibles.

El manifest es una ayuda operativa. Las capacidades deben volver a verificarse cuando cambia la sesión, la cuenta, el entorno o la configuración.

## Handoff basado en capacidades

Una `Execution Task` o `Wiki Update Task` debe indicar:

- capacidades requeridas;
- herramienta sugerida, si corresponde;
- fuentes que debe leer;
- zonas que puede modificar;
- operaciones prohibidas;
- acciones que requieren confirmación;
- evidencia esperada;
- alternativa cuando una capacidad falte.

Ejemplo:

```text
Capacidades requeridas
- leer repositorio de wiki;
- crear branch;
- modificar Markdown;
- ejecutar validador de enlaces;
- abrir pull request.

No requerido
- acceso a producción;
- administración de permisos;
- acceso a base de datos.
```

## Capacidades conversacionales y de ejecución

Un asistente conversacional puede comprender, sintetizar y preparar instrucciones sin disponer de acceso físico al repositorio.

Un coding agent puede modificar archivos solo si dispone de:

- acceso real;
- rutas autorizadas;
- operación de escritura;
- contexto mínimo;
- criterios de aceptación;
- condiciones de detención.

Esta separación permite que GPT, Gemini o Claude actúen como Project Orchestrator y que Codex, Antigravity, Claude Code u otra herramienta materialice los cambios.

## Regla principal

```text
No preguntes solo “qué herramienta usamos”.
Pregunta “qué capacidad requiere la tarea, cuál está verificada y qué está autorizado”.
```

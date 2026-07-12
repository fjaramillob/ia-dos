# Terminología

IA-DOS mantiene en inglés algunos términos técnicos ampliamente utilizados, pero los explica en español.

## `Project Orchestrator`

Asistente conversacional utilizado para dirigir y coordinar el proyecto desde ChatGPT, Gemini, Claude u otro entorno equivalente.

Comprende el contexto, separa conversaciones, prepara `Execution Tasks`, selecciona contexto y revisa el retorno de los coding agents.

## `Conversation Space`

Conversación persistente dedicada a un dominio del proyecto, por ejemplo dirección, producto, arquitectura, desarrollo, QA o wiki.

No es una fuente de verdad independiente. Sus resultados durables deben registrarse en la wiki, un issue, un ADR, una `Execution Task` o un pull request.

## coding agent

Herramienta con capacidad de inspeccionar y modificar un repositorio, por ejemplo Codex, Claude Code o Antigravity.

## `repository`

Repositorio versionado donde se almacena código, documentación u otros archivos de un proyecto.

## `branch`

Línea de trabajo separada dentro de Git. Permite realizar cambios sin modificar directamente la versión principal.

## `commit`

Registro versionado de uno o más cambios relacionados.

## `issue`

Elemento utilizado para registrar trabajo pendiente, bugs, propuestas o preguntas dentro de una plataforma como GitHub.

## `pull request`

Solicitud para revisar e incorporar cambios desde una branch antes de agregarlos a la versión principal.

## `AGENTS.md`

Archivo que entrega instrucciones persistentes a los agentes que trabajan dentro de un repositorio.

## LLM Wiki

Base documental en Markdown diseñada para conservar memoria durable, navegable y versionada para personas y modelos de lenguaje.

## `Execution Task`

Unidad de trabajo concreta, acotada, verificable y terminable.

También funciona como base para preparar el prompt que recibe un coding agent.

## `Context Pack`

Conjunto pequeño de documentos o rutas seleccionados para entregar a un asistente o agente solo el contexto necesario para una conversación o tarea.

## `CORE`

Context Pack mínimo y transversal del proyecto. Contiene propósito, estado resumido, restricciones, decisiones vigentes y ubicación de las fuentes de verdad.

## handoff

Traspaso estructurado desde el orquestador hacia un coding agent, o desde el coding agent de regreso al orquestador.

Incluye la tarea, el contexto necesario, límites y el formato esperado de respuesta.

## `guardrail`

Límite o regla que impide acciones inseguras, fuera de alcance o no autorizadas.

## `Definition of Done`

Conjunto de condiciones que deben cumplirse antes de considerar terminado un trabajo.

## `workspace`

Carpeta raíz local que agrupa IA-DOS y los proyectos administrados.

En la documentación en español, IA-DOS utiliza `proyectos/` como nombre recomendado para esa carpeta.

## app

Repositorio o carpeta que contiene la implementación ejecutable del proyecto.

## wiki

Repositorio o carpeta que contiene la memoria durable del proyecto.

## Fuente de verdad

Ubicación canónica donde debe mantenerse un tipo determinado de información.
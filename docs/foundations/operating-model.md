# Modelo operativo

IA-DOS organiza el desarrollo asistido por inteligencia artificial mediante un ciclo simple:

```text
Dirigir
→ entender
→ documentar
→ delimitar
→ ejecutar
→ verificar
→ registrar
```

## 1. Dirigir

El proyecto comienza en una capa de dirección y orquestación.

Puede implementarse mediante un Project de ChatGPT, un Gem de Gemini, un Project de Claude u otro asistente conversacional.

Esta capa debe:

- mantener la visión general del proyecto;
- separar conversaciones por dominio cuando sea útil;
- identificar prioridades y decisiones abiertas;
- distinguir conversaciones exploratorias de decisiones aprobadas;
- convertir necesidades en trabajo estructurado;
- seleccionar el contexto necesario para cada tarea;
- coordinar el retorno de resultados hacia la wiki.

La conversación principal de dirección no debe acumular todos los detalles. Debe saber dónde vive cada tema y cuál es el siguiente paso correcto.

## 2. Entender

Antes de modificar un proyecto, se debe revisar su estado real.

Esto puede incluir:

- propósito del producto;
- estructura del repositorio;
- arquitectura actual;
- decisiones vigentes;
- riesgos;
- pruebas existentes;
- cambios locales pendientes;
- límites de acceso, coste o seguridad.

El objetivo es reducir supuestos.

El orquestador puede consultar la wiki y el repositorio de aplicación. Si no tiene acceso suficiente, debe señalarlo y evitar inventar información.

## 3. Documentar

El contexto importante debe quedar fuera de la conversación.

IA-DOS recomienda una LLM Wiki versionada que contenga, según corresponda:

- visión y alcance;
- usuarios y producto;
- estado actual;
- arquitectura;
- decisiones;
- riesgos;
- fuentes;
- preguntas abiertas;
- Context Packs.

La wiki describe el proyecto. No reemplaza el código ni debe contener secretos.

Las decisiones tomadas en ChatGPT, Gemini u otro asistente deben regresar a la wiki, a un ADR, a un issue o al artefacto canónico correspondiente.

## 4. Delimitar

Antes de pedir una implementación, se define una unidad de trabajo acotada.

La `Execution Task` debe indicar:

- objetivo;
- problema o evidencia inicial;
- contexto mínimo y rutas que deben leerse;
- alcance;
- fuera de alcance;
- archivos o repositorios autorizados;
- guardrails;
- criterios de aceptación;
- pruebas esperadas;
- condiciones de detención;
- documentación que debe actualizarse;
- formato del reporte final.

El orquestador utiliza esta información para preparar un prompt adaptado a Codex, Claude Code, Antigravity u otro coding agent.

## 5. Ejecutar

El coding agent trabaja dentro de los límites declarados.

Durante esta etapa debe:

- inspeccionar antes de modificar;
- leer únicamente el contexto necesario;
- evitar cambios no solicitados;
- no introducir dependencias sin justificación;
- detenerse si falta una decisión importante;
- registrar los archivos modificados;
- devolver un reporte estructurado.

El coding agent no debe recibir automáticamente todo IA-DOS, toda la wiki o todos los proyectos del workspace.

## 6. Verificar

El resultado se comprueba mediante evidencia aplicable al tipo de cambio.

Puede incluir:

- revisión del diff;
- lint;
- typecheck;
- build;
- pruebas unitarias o de integración;
- revisión visual;
- revisión de seguridad;
- prueba manual reproducible;
- capturas o logs relevantes.

No todos los controles aplican a todas las tareas, pero toda tarea debe indicar cómo fue verificada.

El orquestador compara el reporte con la `Execution Task`, identifica faltantes y evita tratar una afirmación del agente como prueba suficiente.

## 7. Registrar

Al cerrar el trabajo se actualiza la fuente de verdad correspondiente:

- código en el repositorio de aplicación;
- decisión en la wiki;
- evidencia en el pull request o reporte;
- estado de la tarea en el issue o mecanismo elegido;
- documentación cuando cambió el comportamiento del sistema;
- Context Pack cuando cambió información transversal o de dominio.

## Arquitectura de trabajo

```text
IA-DOS
    define cómo trabajar

Project Orchestrator
    dirige, separa conversaciones y prepara trabajo

Wiki del proyecto
    explica qué se construye, por qué y cuál es su estado

Repositorio de aplicación
    contiene la implementación

Issues o Execution Tasks
    delimitan el trabajo

Coding agents
    inspeccionan, implementan y prueban

Branches, commits y pull requests
    trazan los cambios

Pruebas y revisiones
    verifican el resultado
```

## Flujo de contexto

```text
IA-DOS
    ↓ contrato operativo
Project Orchestrator
    ↓ CORE + Context Pack + Execution Task
Coding agent
    ↓ código + pruebas + reporte
Project Orchestrator
    ↓ revisión y síntesis
Wiki / issue / ADR / PR
```

## Fuentes de verdad

IA-DOS busca evitar que la misma información se mantenga manualmente en varios lugares.

| Tipo de información | Destino recomendado |
|---|---|
| Propósito y estado del proyecto | Wiki |
| Arquitectura vigente | Wiki |
| Decisión durable | Registro de decisión en la wiki |
| Instrucciones del orquestador | Configuración del Project, Gem o archivo de orquestación |
| Instrucciones para coding agents | `AGENTS.md` |
| Trabajo pendiente | GitHub Issue o mecanismo elegido por el proyecto |
| Alcance del cambio | `Execution Task` |
| Implementación | Repositorio de aplicación |
| Revisión y evidencia del cambio | Pull request o reporte de ejecución |
| Estándar común reutilizable | Repositorio IA-DOS |

La tarea puede enlazar estos artefactos, pero no debe duplicarlos sin necesidad.
# Modelo operativo

IA-DOS organiza el desarrollo asistido por inteligencia artificial mediante un ciclo simple y repetible:

```text
Dirigir
→ explorar
→ decidir
→ delimitar
→ materializar
→ verificar
→ registrar y aprender
```

La documentación y la LLM Wiki acompañan todo el ciclo. No constituyen una fase exhaustiva previa al desarrollo.

## 1. Dirigir

La persona responsable y el Project Orchestrator mantienen propósito, prioridades, restricciones y siguiente resultado.

La conversación principal no debe acumular todos los detalles. Debe saber dónde vive cada tema, qué decisión falta y qué espacio o tarea desbloquea el siguiente paso.

## 2. Explorar

Se revisa la evidencia suficiente para reducir supuestos:

- propósito y usuario;
- estado real del producto;
- repositorios y documentación relevante;
- decisiones vigentes;
- riesgos, accesos y restricciones;
- pruebas o cambios pendientes cuando existan.

Explorar no significa auditar todo. Si falta acceso, debe declararse y no completarse el vacío mediante invención.

## 3. Decidir

Se confirma la decisión mínima que permite avanzar. Puede ser una decisión de producto, comportamiento, arquitectura, alcance o prioridad.

Distingue:

```text
hecho verificado
preferencia
supuesto
propuesta
decisión de trabajo
decisión durable
desconocido
```

Las decisiones durables regresan a la wiki, un ADR o el artefacto canónico correspondiente.

## 4. Delimitar

Antes de modificar un repositorio se define una unidad de trabajo acotada.

La `Execution Task` indica:

- objetivo;
- evidencia o contexto inicial;
- rutas que deben leerse;
- alcance y fuera de alcance;
- archivos o repositorios autorizados;
- criterios de aceptación;
- pruebas y validaciones;
- condiciones de detención;
- documentación que debe actualizarse;
- formato del reporte final.

## 5. Materializar

El coding agent trabaja dentro de los límites declarados.

Debe:

- inspeccionar antes de modificar;
- leer solo el contexto necesario;
- evitar cambios no solicitados;
- detenerse ante una decisión faltante o riesgo crítico;
- modificar únicamente rutas autorizadas;
- ejecutar las validaciones aplicables;
- devolver un `Execution Report`.

La materialización puede afectar código, documentación o LLM Wiki según la tarea autorizada.

## 6. Verificar

El resultado se comprueba mediante evidencia aplicable al cambio:

- revisión del diff;
- lint, typecheck o build;
- pruebas unitarias o de integración;
- revisión visual o manual reproducible;
- revisión de seguridad;
- validación de Markdown, enlaces, YAML o estructura documental;
- capturas y logs relevantes.

El Project Orchestrator compara el resultado con la tarea. La afirmación del agente no reemplaza la evidencia.

## 7. Registrar y aprender

Al cerrar el trabajo se actualiza la fuente de verdad correspondiente:

- implementación en el repositorio de aplicación;
- decisión, estado o arquitectura en la wiki;
- evidencia en el pull request o reporte;
- estado de la tarea en el issue;
- documentación cuando cambió el comportamiento;
- Context Pack cuando cambió información transversal.

La wiki se puebla progresivamente. No necesita actualizarse por cada conversación o cambio menor.

## Arquitectura de trabajo

```text
IA-DOS
    define el método

Persona responsable
    dirige, confirma y autoriza

Project Orchestrator
    organiza, delimita y revisa

Conversation Spaces
    razonan por dominio

Execution Tasks
    delimitan cambios

Coding agents
    inspeccionan, materializan y prueban

Repositorios y Git
    contienen y trazan cambios

Pruebas, PRs y reportes
    verifican resultados

LLM Wiki
    conserva contexto y aprendizaje durable
```

## Flujo de contexto

```text
IA-DOS
    ↓ contrato operativo
Project Orchestrator
    ↓ CORE + Context Pack + Execution Task
Coding agent
    ↓ cambios + pruebas + Execution Report
Project Orchestrator y persona responsable
    ↓ revisión, decisión y aprobación
Wiki / issue / ADR / PR
```

## Fuentes de verdad

| Tipo de información | Destino recomendado |
|---|---|
| Propósito y estado del proyecto | LLM Wiki |
| Arquitectura vigente | LLM Wiki |
| Decisión durable | ADR o registro de decisión en la wiki |
| Instrucciones del orquestador | Configuración del Project, Gem o archivo de orquestación |
| Instrucciones para coding agents | `AGENTS.md` |
| Trabajo pendiente | GitHub Issue o mecanismo elegido |
| Alcance del cambio | `Execution Task` |
| Implementación | Repositorio de aplicación |
| Revisión y evidencia | Pull request y `Execution Report` |
| Estándar reutilizable | Repositorio IA-DOS |

Los artefactos pueden enlazarse, pero no deben duplicarse sin necesidad.

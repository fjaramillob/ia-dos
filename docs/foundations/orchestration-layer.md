# Capa de orquestación conversacional

IA-DOS no organiza solamente el trabajo de los agentes que escriben código. También organiza la capa de conversación desde la que una persona dirige el proyecto.

Para muchos usuarios, especialmente quienes no son programadores expertos, esta capa será la interfaz principal del desarrollo.

## Qué es

La capa de orquestación conversacional puede implementarse como:

- un Project de ChatGPT;
- un Gem de Gemini;
- un Project de Claude;
- una conversación persistente;
- un asistente personalizado;
- otro entorno equivalente.

Su función es comprender el proyecto, ordenar el contexto, separar conversaciones útiles, registrar decisiones y transformar necesidades en trabajo ejecutable para coding agents.

## Qué consume

El orquestador puede recibir:

1. el repositorio IA-DOS, para conocer la forma de trabajo;
2. la wiki del proyecto, para conocer propósito, estado, decisiones y restricciones;
3. el repositorio de aplicación, para consultar la implementación cuando la herramienta tenga acceso;
4. instrucciones específicas del usuario o del equipo.

El repositorio IA-DOS define cómo trabajar. La wiki y la aplicación explican el proyecto concreto.

## Qué produce

La capa conversacional transforma conversaciones en artefactos durables como:

- decisiones;
- actualizaciones de la wiki;
- `Execution Tasks`;
- prompts para Codex, Claude Code, Antigravity u otros coding agents;
- criterios de aceptación;
- planes de prueba;
- issues;
- ADR;
- prioridades y siguientes pasos.

Una conversación no debe quedar como único lugar donde vive una decisión importante.

## Arquitectura

```text
Usuario
   ↓
Project Orchestrator
ChatGPT / Gemini / Claude
   │
   ├── consulta IA-DOS
   ├── consulta la wiki
   ├── consulta la app cuando corresponde
   ├── separa conversaciones por dominio
   └── prepara trabajo estructurado
            ↓
Execution Task + contexto mínimo
            ↓
Codex / Claude Code / Antigravity
            ↓
Código + pruebas + reporte
            ↓
Orquestador revisa evidencia
            ↓
Wiki / issue / ADR / PR actualizados
```

## Conversation Spaces

Un `Conversation Space` es una conversación persistente dedicada a un dominio del proyecto.

La estructura inicial recomendada es:

```text
00 — Dirección y orquestación
10 — Producto y UX
20 — Arquitectura y datos
30 — Desarrollo
40 — QA y seguridad
90 — Wiki y memoria
```

No todos los proyectos necesitan todas estas conversaciones. Un proyecto pequeño puede comenzar con una sola conversación de dirección y abrir espacios adicionales cuando el contexto empiece a mezclarse.

## Conversación principal

La conversación `00 — Dirección y orquestación` mantiene la visión transversal.

Debe saber:

- cuál es el estado general;
- qué decisiones están abiertas;
- cuál es la prioridad actual;
- qué Conversation Space debe tratar cada tema;
- qué información debe regresar a la wiki;
- qué trabajo puede convertirse en una `Execution Task`;
- qué evidencia falta antes de cerrar una tarea.

No debe reemplazar los espacios especializados ni acumular todos los detalles técnicos.

## Entrada estructurada al desarrollo

El principal resultado del orquestador es convertir una necesidad expresada en lenguaje natural en una entrada de desarrollo controlada.

```text
Conversación
    ↓
Decisión o necesidad clara
    ↓
Execution Task
    ↓
Prompt optimizado para el coding agent
```

El prompt debe incluir:

- objetivo;
- contexto mínimo;
- rutas que debe consultar;
- alcance;
- fuera de alcance;
- repositorio y zonas autorizadas;
- guardrails;
- criterios de aceptación;
- pruebas;
- condiciones de detención;
- documentación a actualizar;
- formato del reporte final.

## Optimización de contexto

El orquestador no debe enviar el repositorio completo ni toda la conversación en cada handoff.

Debe utilizar:

```text
CORE
+
un Context Pack principal
+
opcionalmente un Context Pack secundario
+
la Execution Task
```

`CORE` contiene solamente la información transversal necesaria:

- propósito del proyecto;
- usuario principal;
- estado actual resumido;
- restricciones;
- decisiones vigentes relevantes;
- ubicación de las fuentes de verdad.

Los demás `Context Packs` contienen información de dominios como producto, arquitectura, seguridad, aplicación o QA.

## Flujo de retorno

El coding agent debe devolver un reporte estructurado.

El orquestador debe:

1. comparar el resultado con la `Execution Task`;
2. revisar qué evidencia fue entregada;
3. identificar riesgos o trabajo pendiente;
4. no asumir que una afirmación equivale a una prueba;
5. indicar qué información debe actualizarse en la wiki;
6. decidir con el usuario el siguiente paso.

## Regla de fuente de verdad

- La conversación dirige y coordina.
- La wiki conserva contexto y decisiones.
- La aplicación conserva la implementación.
- El issue o la `Execution Task` conserva el alcance del trabajo.
- El pull request o reporte conserva la evidencia del cambio.

IA-DOS conecta estas capas para que una conversación externa se convierta en un input útil, acotado y trazable para el desarrollo.
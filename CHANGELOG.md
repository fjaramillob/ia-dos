# Changelog

Todos los cambios relevantes de IA-DOS se registrarán en este archivo.

El proyecto utiliza versionado semántico durante su etapa experimental.

## Unreleased

### Added

- definición inicial de propósito y alcance;
- público objetivo;
- principios;
- capa de orquestación conversacional;
- instrucciones para el `Project Orchestrator`;
- prompt universal de inicialización del orquestador;
- plantilla opcional de instrucciones persistentes para Projects, Gems y espacios equivalentes;
- `Project Intake Brief` para entregar contexto inicial sin formularios pesados;
- `IA-DOS Project Orchestrator Pack` para plataformas sin acceso directo a GitHub;
- estructura progresiva de Conversation Spaces con núcleo mínimo y dominios opcionales;
- regla explícita `1 Execution Task → 1 ejecución acotada → 1 Execution Report`;
- clasificación basada en el producto objetivo y no en sistemas anteriores relacionados;
- separación explícita entre `00` y `90` cuando la plataforma permite varias conversaciones;
- guía de primera respuesta accionable con nombre recomendado del chat, siguiente acción humana y máximo tres preguntas prioritarias;
- recomendación por defecto de GitHub Issues como fuente canónica de tareas cuando existe repositorio remoto;
- gestión explícita de estados entre hechos, preferencias, propuestas, decisiones conversacionales y decisiones durables;
- regla de una decisión principal por turno y alternativas claramente no confirmadas;
- gate de salida para `00 — Dirección y definición` con aprobación explícita antes de crear `90 — Wiki y memoria`;
- prohibición de describir al usuario como bloqueo o de repetir el onboarding inicial en cada turno;
- principios LLM Wiki inspirados en la propuesta de Andrej Karpathy;
- recorridos iniciales para proyectos nuevos y existentes;
- guía inicial de construcción de la LLM Wiki;
- guía de preparación del workspace local;
- guía manual de instalación de IA-DOS para Windows, macOS y Linux;
- prompt para que un agente instale IA-DOS con validaciones y condiciones de detención;
- guía para crear formalmente un proyecto nuevo dentro del workspace;
- guía para incorporar un proyecto existente sin alterar su historia ni moverlo a ciegas;
- prompts operativos para crear o incorporar proyectos con condiciones de detención;
- manifiesto `.ia-dos.yaml` para declarar adopción;
- plantilla `AGENTS.md` para repositorios de aplicación;
- wiki starter con `project-brief`, estado actual, arquitectura, registro, fuentes, decisiones, tareas y `CORE`;
- guía para aplicar y verificar las plantillas mínimas de adopción;
- plantilla de `Execution Task`;
- plantilla de `Execution Report`;
- guía de handoff entre Project Orchestrator y coding agent;
- prompt de ejecución acotada para coding agents;
- reglas explícitas de sanitización para evitar información personal, laboral o de proyectos reales en el repositorio público;
- modelo operativo;
- modelo de adopción;
- responsabilidades humanas, del orquestador y de los coding agents;
- fuentes de verdad;
- terminología;
- gobierno;
- guía de contribución;
- política de seguridad;
- roadmap inicial;
- referencias de influencias de diseño.

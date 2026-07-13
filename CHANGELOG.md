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
- guía de primera respuesta accionable con nombre recomendado del chat y siguiente acción humana;
- distinción explícita entre fuente canónica y fuente operativa de IA-DOS;
- guía conversacional para utilizar lenguaje natural y mantener los niveles metodológicos como andamiaje interno;
- regla reforzada de una decisión principal por turno, sin mezclar decisiones distintas;
- prohibición de inventar porcentajes, días, semanas o umbrales sin evidencia;
- niveles progresivos de definición desde resultado esperado hasta implementación técnica;
- principio de decisión mínima, reversible y tecnológicamente neutral;
- guía para definir ciclos de vida, invariantes, permisos por rol y trazabilidad antes de diseñar interfaz o implementación;
- diferenciación explícita entre corrección, anulación, reversión, eliminación y ajuste;
- modelo de captura del alma del proyecto mediante propósito, usuario, problema, promesa, principios y primer resultado;
- gate mínimo de alineación para comenzar a organizar y construir sin exigir una especificación completa;
- `Launch Mode` para responder a la intención explícita del usuario de avanzar;
- estrategia de avance basada en vertical slices, arquitectura suficiente, ejecución verificable y aprendizaje;
- secuencia explícita de apertura de Conversation Spaces: `90` y `10`, luego `20`, y finalmente `30`;
- convención de títulos limpios sin repetir el nombre del proyecto dentro de un Project o Gem dedicado;
- plantilla `Conversation Space Handoff` para transferir contexto entre chats que no comparten historial;
- obligación de declarar en cada handoff el espacio de destino y evitar reiniciar onboarding o reclasificar el proyecto;
- handoff de salida obligatorio entre Producto, Arquitectura y Ejecución;
- regla especial para que `20 — Arquitectura y stack` no herede automáticamente tecnologías de sistemas anteriores;
- creación temprana de `90 — Wiki y memoria` como memoria viva, no como etapa final de la definición;
- regla para tratar hipótesis, preguntas abiertas y decisiones por explorar como trabajo futuro y no como bloqueo;
- criterio para resolver decisiones delegadas a mejores prácticas mediante una recomendación provisional y avance controlado;
- recorridos iniciales para proyectos nuevos y existentes;
- guía inicial de construcción de la LLM Wiki;
- principios LLM Wiki inspirados en la propuesta de Andrej Karpathy;
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
# Changelog

Todos los cambios relevantes de IA-DOS se registrarán en este archivo.

El proyecto utiliza versionado semántico durante su etapa experimental.

## Unreleased

### Changed

- evolucionada la heurística de granularidad de `Execution Task` desde “pequeña y verificable” hacia un outcome definido, cohesivo, acotado y verificable bajo una frontera estable de autoridad; una misma Task puede contener revalidación, implementación, verificaciones, Git, delivery y smoke cuando todas las fases sirven al mismo outcome;
- incorporado `Authority Envelope` como semántica dentro de `Execution Task`, sin crear un nuevo Artifact Type: una acción sensible no declarada permanece no autorizada y una acción explícitamente declarada, con gates cumplidos y frontera estable, no exige otra ida y vuelta humana por rutina;
- aclarado que un `Implementation Plan` sigue siendo propuesta y no se autoaprueba, pero el Cycle Owner puede adoptarlo dentro de autoridad delegada sin una aprobación humana adicional automática; la persona responsable interviene ante cambios materiales de dirección, autoridad, producción, datos, seguridad, cumplimiento, coste, riesgo o impacto relevante;
- reforzada la compresión de contexto mediante `Embedded Contract`, `Required Reading` y `Reference`; una Task es suficientemente autocontenida cuando `Task + Required Reading` permiten ejecutarla sin depender de conversaciones previas;
- agregado `<TASK-ID>-CHECKPOINT.md` como sidecar operacional opcional para continuidad de tareas largas o cambio de Coding Agent, sin autoridad propia ni nuevo Artifact Type;
- fijada la semántica `Execution Resume = Task original + delta del bloqueo resuelto`, conservando Task ID mientras objetivo, alcance, autoridad, seguridad y arquitectura no cambien;
- simplificado `Execution Report` hacia un formato evidence-first y proporcional que prioriza `Outcome`, `Evidence`, `Actual Scope`, `Acceptance`, `Deviations` y `Final State`, evitando repetir la Task;
- simplificados `Manual Artifact Launcher` y `Caveman Return` para que el launcher sólo localice la Task y el retorno conversacional no repita evidencia que ya vive en el output completo materializado;
- reforzado Exchange como capacidad opcional, provider-agnostic, filesystem-first y pasiva; Google Drive, OneDrive, Dropbox, Syncthing, NAS o carpeta local/manual son sólo mecanismos posibles de transporte y no forman parte de la semántica del core;
- redefinidas las carpetas de Exchange: `inbox/` contiene artifacts operativamente activos destinados a Coding Agents, `outbox/` outputs pendientes de consumo o aún requeridos por trabajo activo y `archive/` cold storage operacional por trazabilidad; `folder ≠ workflow state` y `archive ≠ aprobado/completado/memoria durable/repositorio de documentos vivos`;
- incorporada alineación condicional con IA-DOS para Conversation Spaces nuevos, retomados después de un cambio relevante del método o con reglas obsoletas, sin reiniciar onboarding ni releer el framework completo;
- documentada la actualización segura de una instalación local existente mediante `git fetch`, comprobación de divergencia y `git pull --ff-only`; se explicita que `git status` previo al fetch no demuestra que GitHub no tenga commits nuevos y que `reset --hard`, `clean`, merges/rebases implícitos y force push no son rutina de actualización;
- Archify permanece fuera del core: puede evaluarse posteriormente como capacidad opcional de visualización técnica y Supporting Artifact, no como dependencia ni Artifact Type.

- fijada la frontera de transporte entre Conversation Spaces: `Specialist Handoff` se entrega inline, autocontenido y copiable; no requiere `.md`, Exchange, path ni `Manual Artifact Launcher`;
- aclarado que Exchange permanece como pasarela pasiva y opcional hacia/desde Coding Agents y no participa en routing entre Conversation Spaces;
- ejecutada una auditoría integral del repositorio vigente para alinear contratos, onboarding, prompts, templates, discoverability, validaciones y distribución offline con el modelo consolidado;
- reforzada la frontera entre responsabilidad humana y `Cycle Owner`: el Conversation Space gobierna dentro de autoridad delegada y no sustituye aprobación humana cuando cambian dirección, autoridad, riesgo o impacto relevante;
- eliminado de superficies vigentes cualquier requisito residual para que `Execution Report` recomiende memoria durable, elija la decisión de gobierno posterior o proponga automáticamente la siguiente unidad;
- eliminada la creación implícita de una conversación de ejecución por cada Planning Task; las `Execution Cells` pueden reutilizar su conversación activa mientras siga respondiendo bien y cada tarea vuelve a declarar permisos;
- alineados `Environment Preflight` y `Execution Resume` con `LISTO PARA EJECUCIÓN` y con la preservación obligatoria de objetivo, alcance, autoridad, seguridad y arquitectura;
- corregidas rutas rápidas de orquestación para evaluar `Memory Bootstrap Gate` y readiness indispensable antes de autorizar ejecución;
- consolidada la distinción `memoria durable` como responsabilidad funcional y `LLM Wiki` como su materialización durable, portable y navegable cuando se adopta;
- corregida la instalación local de IA-DOS para que cree únicamente una referencia `00-ia-dos/` y no imponga ni cree topología app/wiki/Exchange del proyecto;
- marcadas las validaciones de Fase 6 como evidencia histórica fechada para evitar interpretarlas como garantía permanente del repositorio actual;
- regenerado el `Current Offline Pack` con los contratos vigentes de la auditoría integral de `v0.1.0-alpha.3`;
- simplificado `Exchange` como pasarela pasiva y opcional de archivos Markdown entre Conversation Agents y Code Agents;
- eliminado cualquier rol de Exchange en generación o validación de IDs, nombres de archivo, templates, estados, permisos, backlog, memoria, decisiones o workflow;
- eliminado de los contratos vigentes el modelo de templates propios de Exchange: la `Execution Task` y el `Execution Report` canónicos son los mismos artefactos que atraviesan Exchange;
- trasladada la responsabilidad del `Task ID` al Conversation Agent que construye la tarea; el Execution Report reutiliza ese mismo ID por contrato;
- reducido Exchange a `inbox/`, `outbox/` y `archive/` como ubicaciones de intercambio o conservación, no estados del método;
- actualizado el modelo de adopción para registrar Exchange únicamente como recurso opcional y no como fuente de tareas;
- alineados onboarding, workspace, adopción, terminología e instrucciones persistentes con esta frontera pasiva de Exchange;
- definido el `Memory Bootstrap Gate` para impedir que una nueva unidad dependa de conocimiento relevante que exista únicamente en conversaciones, sin imponer una Wiki completa por ceremonia;
- modernizado el Wiki Starter hacia un checkpoint Markdown mínimo con `00-home.md`, `project-brief.md`, `status/current-state.md`, `decisions/`, `sources/` y `AGENTS.md`;
- retirados del Wiki Starter vigente `tasks/`, `context-packs/`, `CORE`, `log.md` y la página de arquitectura vacía; los proyectos existentes pueden conservar esos patrones cuando sigan aportando valor;
- alineada la memoria durable con Markdown estándar, enlaces relativos canónicos y consumo desde Obsidian sin dependencia de wikilinks o plugins;
- conectado el onboarding y la compresión de contexto con el Memory Bootstrap Gate para evitar repetir indefinidamente contexto chat-only;
- unificado `00 — Dirección y orquestación` como nombre canónico del espacio inicial;
- unificado `Execution Task` como contrato semántico único, independientemente de si se transporta por chat, archivo, issue o Exchange;
- estados canónicos de Execution Report: `COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO`;
- aclarado que `Execution Cell` aporta continuidad operacional y no sustituye `Destination Role`, `Cycle Owner` ni permisos por tarea;
- aclarado que `Cycle ID` puede ser `NO APLICA` cuando no existe un ciclo separado;
- actualizado el fallback offline para mantener sincronizados los contratos vigentes.

### Added

- guía `Crear o conectar Exchange` para configurar una pasarela de artifacts `.md` sin protocolo semántico propio;
- contrato `Memory Bootstrap Gate` con resultados `PASS` y `BOOTSTRAP REQUIRED`;
- `Execution Cell` como contexto de continuidad de ejecución definido por proyecto;
- política para mantener una sola conversación activa por Execution Cell mientras siga respondiendo bien;
- regla explícita de que reutilizar una conversación no acumula permisos entre tareas;
- Exchange como pasarela opcional con topología mínima `inbox/`, `outbox/` y `archive/`;
- esquema recomendado de `Task ID` `{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}` asignado por el Conversation Agent;
- guía de memoria durable portable para GitHub, Markdown, Obsidian y consumo selectivo por agentes;
- distinción entre contexto embebido, referencias y lectura requerida;
- guía de avance concreto y transición a coding agents;
- modelo operativo para conectores, MCP, herramientas nativas, archivos adjuntos y acceso local;
- separación explícita entre capacidad, permiso, autorización, ejecución y verificación;
- modelo de capacidades con estados `verified`, `declared`, `unavailable`, `unknown`, `blocked` y `degraded`;
- reglas de mínimo privilegio, contexto mínimo y degradación segura;
- plantilla opcional `Capability Manifest`;
- criterios de seguridad y trazabilidad para integraciones, credenciales y acciones sensibles;
- definición de `90 — Wiki y memoria` como Conversation Space de gobierno y síntesis, no como ejecutor físico;
- guía operativa para crear y mantener la LLM Wiki mediante coding agents;
- plantilla especializada `Wiki Update Task` como perfil documental de Execution Task;
- método de trabajo maestro basado en `entender → decidir → delimitar → materializar → verificar y aprender`;
- separación explícita entre dirección, razonamiento, materialización y verificación;
- guía dedicada para coding agents;
- definición inicial de propósito y alcance, público objetivo, principios, capa de orquestación conversacional e instrucciones del Project Orchestrator;
- prompt universal de inicialización del orquestador;
- plantilla opcional de instrucciones persistentes para espacios equivalentes;
- `Project Intake Brief` para contexto inicial sin formularios pesados;
- `Current Offline Pack` para plataformas sin acceso directo a GitHub;
- estructura progresiva de Conversation Spaces con dominios bajo demanda;
- clasificación basada en el producto objetivo y no en sistemas anteriores relacionados;
- guía conversacional para lenguaje natural y niveles metodológicos como andamiaje interno;
- regla para no inventar porcentajes, días, semanas o umbrales sin evidencia;
- guía para ciclos de vida, invariantes, permisos por rol y trazabilidad;
- recorridos iniciales para proyectos nuevos y existentes;
- guía manual de instalación de IA-DOS para Windows, macOS y Linux;
- prompt para instalar IA-DOS con validaciones y condiciones de detención;
- manifiesto `.ia-dos.yaml` para declarar adopción;
- plantilla `AGENTS.md` para repositorios de aplicación;
- plantilla de `Execution Task` y `Execution Report`;
- guía de handoff entre Project Orchestrator y coding agent;
- reglas explícitas de sanitización para evitar información sensible o de proyectos reales en el repositorio público;
- modelo operativo, modelo de adopción, responsabilidades, fuentes de verdad, terminología, gobierno, contribución, seguridad, roadmap y referencias de diseño.

# Preguntas de validación

Durante la etapa alpha, cada revisión importante de IA-DOS debe poder responder estas preguntas con evidencia del repositorio y, cuando corresponda, de proyectos reales.

## Comprensión

- ¿Una persona no experta entiende qué es IA-DOS y qué no es?
- ¿Se distingue el framework del proyecto que lo adopta?
- ¿Se entiende la diferencia entre persona responsable, Project Orchestrator, Conversation Space, Cycle Owner y coding agent?
- ¿Los Conversation Spaces aparecen como contextos bajo demanda y no como fases obligatorias?

## Memoria

- ¿Se distingue `memoria durable` como función de `LLM Wiki` como materialización?
- ¿La ausencia de una Wiki separada puede seguir siendo válida?
- ¿El Memory Bootstrap Gate evita dependencia chat-only sin imponer documentación por ceremonia?
- ¿Los coding agents reciben sólo contexto durable necesario y lecturas explícitas?
- ¿TASK/REPORT, logs, diffs y transcripciones permanecen fuera de la memoria vigente por defecto?

## Planificación, readiness y ejecución

- ¿Una unidad lista puede ir directamente a Execution Task?
- ¿Una incertidumbre técnica real puede ir a Planning Task en solo lectura?
- ¿Readiness indispensable desconocido deriva a Environment Preflight antes de escribir?
- ¿Sólo `LISTO PARA EJECUCIÓN` habilita aprobar o reanudar escritura?
- ¿Execution Resume se invalida si cambia objetivo, alcance, autoridad, seguridad o arquitectura?
- ¿Una Execution Cell puede reutilizarse sin heredar permisos ni crear una conversación por tarea?
- ¿La política de conversaciones de Planning permanece abierta sin inferirse de Execution Cells?

## Evidencia y responsabilidad

- ¿El Execution Report describe evidencia mediante estados canónicos y `Atención requerida`?
- ¿El coding agent evita seleccionar aprobación, corrección, reversión, escalamiento o memoria posterior?
- ¿El Cycle Owner actúa sólo dentro de autoridad delegada?
- ¿La persona responsable conserva la aprobación final en decisiones relevantes?
- ¿Se distingue claramente plan, autorización, ejecución, verificación y estado durable?

## Exchange

- ¿Exchange sigue siendo una pasarela pasiva de `.md` y nada más?
- ¿Los IDs siguen siendo asignados por el Conversation Agent y no por Exchange?
- ¿No existe un backlog, workflow, estado automático o sistema de permisos accidental dentro de Exchange?

## Portabilidad y distribución

- ¿IA-DOS sigue siendo independiente de proveedor, editor, stack y topología?
- ¿El Current Offline Pack reproduce los contratos vigentes del repositorio?
- ¿Los bundles históricos están claramente aislados de onboarding nuevo?
- ¿Una adopción nueva puede funcionar con repositorio remoto, referencia local o contrato embebido sin copiar todo IA-DOS dentro del producto?

## Calidad del estándar

- ¿La documentación evita términos históricos presentados como vigentes?
- ¿Los templates y prompts copiados directamente a agentes coinciden con la documentación canónica?
- ¿El framework reduce repetición y complejidad en vez de agregar ceremonia?
- ¿Los cambios nuevos surgieron de una necesidad observada o una contradicción verificable?
- ¿El método sigue funcionando sin introducir herramientas o automatizaciones no necesarias?

Una respuesta negativa debe producir una corrección acotada o una decisión explícita; no justifica por sí sola ampliar la arquitectura de IA-DOS.

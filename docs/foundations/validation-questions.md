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
- ¿La Memory Policy separa correctamente `NONE | CONDITIONAL | REQUIRED`?
- ¿Memory Stewardship distingue `LOCAL | 90_STRUCTURAL | NO APLICA`?
- ¿Los triggers condicionales los define el Cycle Owner en vez de inferirlos el Coding Agent?
- ¿Un impacto estructural pendiente usa `ROUTE_TO_90` y una Wiki Task ya custodiada por 90 termina `UPDATED`?
- ¿current-state sigue siendo snapshot/índice compacto en vez de historial acumulativo?
- ¿Un cambio de estado publicado mantiene un Operational Baseline durable aunque no amerite cambio semántico?
- ¿Se distinguen Repository HEAD y Production Commit cuando no coinciden?
- ¿Un Coding Agent nuevo puede ponerse al día con repo + Wiki relevante + Task vigente sin reconstruir chats?
- ¿Los outcomes menores pueden diferirse y consolidarse sin perder el baseline operacional?

## Planificación, readiness y ejecución

- ¿Un outcome definido va por defecto a Execution Task con Revalidate y planificación interna?
- ¿Planning separado aparece sólo ante una decisión material todavía no resuelta?
- ¿Environment Preflight separado aparece sólo cuando readiness debe conocerse antes de conceder autoridad sensible, la capacidad misma es objeto de evaluación o requiere otro actor/entorno?
- ¿La Execution Task declara Protected Invariants, Adaptation Authority y Protected Boundaries?
- ¿Con BOUNDED el Coding Agent puede diagnosticar, reparar y safe-retry fallos reversibles sin una nueva Task?
- ¿Execution Resume se reserva para bloqueo externo/interrupción real y se invalida si cambian outcome, invariantes, fronteras, alcance, autoridad, seguridad o arquitectura?
- ¿Una Execution Cell puede reutilizarse sin heredar permisos ni crear una conversación por tarea?
- ¿La política de conversaciones de Planning permanece abierta sin inferirse de Execution Cells?

## Evidencia y responsabilidad

- ¿El Execution Report describe evidencia mediante estados canónicos y `Atención requerida`?
- ¿El coding agent evita seleccionar aprobación, corrección, reversión o escalamiento y limita la memoria a la política/triggers autorizados?
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

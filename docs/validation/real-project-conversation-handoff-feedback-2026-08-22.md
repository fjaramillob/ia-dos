# Feedback de adopción real — handoff entre Conversation Spaces

**Fecha:** 2026-08-22  
**Estado:** CORREGIDO EN BRANCH / PENDIENTE DE REVIEW E INTEGRACIÓN

## Contexto

Durante uso real de IA-DOS en un proyecto activo, un Conversation Space detectó que la decisión dominante había pasado de producto/UX a operación/entrega y preparó un `Specialist Handoff` hacia otro Conversation Space.

El contenido semántico del handoff era correcto, pero el Orchestrator lo materializó como archivo `.md`, indicó guardarlo en un `Exchange/inbox/` y pidió pegar en la conversación destino un prompt que apuntaba al path del archivo.

La persona responsable corrigió explícitamente esa conducta: las derivaciones entre Conversation Spaces se consumen como texto copiable, no mediante Exchange.

## Fricción observada

La documentación vigente decía que `Specialist Handoff` tenía como receptor un Conversation Space y que Exchange era una pasarela pasiva de Markdown, pero no hacía suficientemente explícita la frontera física de transporte.

Eso permitió esta interpretación incorrecta:

```text
Conversation Space
→ Specialist Handoff.md
→ Exchange/inbox
→ prompt con path
→ Conversation Space destino
```

Ese flujo introduce ceremonia innecesaria y confunde dos planos distintos:

- routing y gobierno conversacional;
- intercambio físico de artefactos con Coding Agents.

## Contrato corregido

```text
Conversation Space → Conversation Space
→ Specialist Handoff inline, autocontenido y copiable
→ la persona copia/pega el bloque en el Conversation Space destino
→ no requiere `.md`, Exchange, path ni Manual Artifact Launcher
```

Separadamente:

```text
Conversation Space → Coding Agent
→ Planning Task | Environment Preflight | Execution Task | Execution Resume
→ puede entregarse por chat o materializarse como `.md`/Exchange según el contrato de entrega
```

## Consecuencias

- `Specialist Handoff` sigue siendo un Artifact Type; cambia la claridad de su transporte normativo, no su semántica.
- Exchange sigue siendo pasivo y opcional.
- Exchange no se convierte en mecanismo de routing entre Conversation Spaces.
- `Manual Artifact Launcher` permanece asociado a consumo manual de artefactos por Coding Agents.
- Una copia `.md` de un handoff puede existir sólo como auxiliar explícitamente solicitado o por una convención local separada de archivo; nunca como requisito de la transferencia.
- No se crean nuevos Artifact Types, roles, gates, estados ni automatización.

## Superficies alineadas

- `README.md`
- `templates/conversation-space-handoff.template.md`
- `templates/project-instructions.template.md`
- `prompts/getting-started/initialize-project-orchestrator.md`
- `docs/orchestration/topic-routing-registry.md`
- `docs/orchestration/typed-artifact-routing.md`
- `docs/foundations/conversational-guidance.md`
- `docs/execution/execution-cells-and-exchange.md`
- `ORCHESTRATOR.md`
- `AGENTS.md`
- `bundles/ia-dos-current-offline-pack.md`

## Hallazgos durante review

La primera revisión de la PR detectó que la plantilla operativa de `Specialist Handoff` no había recibido efectivamente el cambio pese a que otras superficies ya asumían esa alineación, y que `templates/project-instructions.template.md` seguía dejando Exchange demasiado genérico.

Ambas superficies fueron corregidas antes de una nueva revisión.

La segunda revisión detectó que `prompts/getting-started/initialize-project-orchestrator.md` puede operar como bloque autocontenido cuando la plataforma no usa instrucciones persistentes y todavía no enseñaba la frontera inline. También fue corregido para incluir `Specialist Handoff` en el gate, separar explícitamente ambos transportes y prohibir Exchange/launcher para routing conversacional.

La tercera revisión detectó que `README.md`, por ser una entrada operativa principal, todavía presentaba `Specialist Handoff` y Exchange sin la frontera de transporte explícita. Se corrigió para declarar el handoff inline en tipos de artefacto, Exchange y quick start.

Estos hallazgos confirman que la frontera de transporte debe existir tanto en contratos canónicos como en todas las superficies que un Orchestrator puede consumir de forma autónoma.

## Criterio de validación

La mejora se considera coherente cuando un agente que consulte cualquiera de las superficies operativas principales pueda distinguir sin inferencias:

```text
handoff conversacional
→ inline y copiable

artefacto hacia Coding Agent
→ chat o Exchange según contrato
```

El uso de Exchange por un proyecto no debe inducir automáticamente a convertir los handoffs entre Conversation Spaces en archivos.
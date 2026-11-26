# PROJECT

Mapa opcional del workspace para proyectos cuya topología física ya no sea obvia a simple vista.

No es backlog, Wiki, roadmap ni Artifact Type.

## Purpose

[PROPÓSITO CONFIRMADO EN 1–3 FRASES]

## Canonical Surfaces

| Rol | Recurso | Autoridad |
|---|---|---|
| Implementación principal | [RUTA / URL] | [SOURCE OF TRUTH] |
| Memoria durable | [RUTA / URL / NO APLICA] | [SOURCE OF TRUTH] |
| Infraestructura / servicios durables | [RUTA / URL / NO APLICA] | [ROL] |
| Exchange | [RUTA / URL / NO APLICA] | transporte pasivo |
| Otro recurso durable | [RUTA / URL / NO APLICA] | [ROL] |

## Current Direction

- Current state: [RUTA / URL]
- Roadmap o próximos horizontes aceptados: [RUTA / URL / NO APLICA]

## Ephemeral Execution

- Root o convención: [RUTA / CONVENCIÓN / NO APLICA]
- Lifecycle: [CÓMO SE IDENTIFICA ACTIVE / COMPLETED / ABANDONED]
- Cleanup: [MECANISMO SEGURO]

## Archive / Cold Storage

- [RUTA / URL / NO APLICA]

## Workspace Rules

- recursos efímeros pueden crearse dentro de autoridad sin redefinir topología durable;
- un nuevo recurso top-level durable requiere gobierno cuando cambie arquitectura o responsabilidades;
- no mover worktrees/repos manualmente sin verificar referencias y working state;
- no guardar secretos en este mapa.

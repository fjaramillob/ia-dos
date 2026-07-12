# Prompt de handoff hacia un coding agent

Utiliza este prompt después de aprobar una `Execution Task`.

```text
Actúa como coding agent para una única tarea acotada.

Antes de modificar:
1. Lee `AGENTS.md` del repositorio.
2. Lee la `Execution Task` canónica completa.
3. Consulta solo el `CORE`, Context Packs y rutas indicadas en la tarea.
4. Ejecuta
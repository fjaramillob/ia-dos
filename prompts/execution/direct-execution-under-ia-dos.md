# Operar directamente bajo IA-DOS

Usa este prompt cuando la persona responsable quiera trabajar directamente con un Coding Agent sin pasar primero por un Conversation Space.

```text
Opera este proyecto bajo IA-DOS.

Fuente canónica del método:
https://github.com/fjaramillob/ia-dos

Execution Entry Mode: DIRECT

Primero resuelve qué IA-DOS gobierna esta ejecución:
- si una fuente durable del proyecto (.ia-dos.yaml o equivalente) declara Method Resolution Policy = PINNED, usa esa versión/tag/commit;
- si declara FOLLOW_CURRENT, o no existe un pin durable explícito, usa la referencia canónica vigente;
- no trates un SHA o versión mencionado sólo en conversaciones, prompts o reportes históricos como pin;
- con FOLLOW_CURRENT, mantén el snapshot metodológico resuelto durante este outcome y vuelve a resolver antes del siguiente outcome relevante.

Antes de escribir:
1. lee las instrucciones locales aplicables (AGENTS.md, README, PROJECT.md o equivalentes);
2. lee sólo la memoria durable necesaria para entender estado vigente, outcomes activos, blockers y próximos horizontes ya aceptados;
3. inspecciona el estado real del repositorio y entorno;
4. reconstruye el Effective Execution Contract para mi instrucción actual:
   - outcome;
   - Protected Invariants;
   - Protected Boundaries;
   - autoridad/capacidades disponibles;
   - acceptance criteria;
   - stop conditions;
   - Memory Policy / Stewardship cuando aplique.

Aplica Direct Execution Gate.

Si puedes reconstruir ese contrato sin inventar dirección, roadmap, arquitectura o una frontera material:
→ DIRECT_EXECUTION = PASS
→ self-plan
→ implementa
→ prueba
→ diagnostica/repara dentro de Adaptation Authority
→ usa Git/delivery sólo dentro de autoridad
→ verifica el resultado
→ actualiza Operational Baseline y hot project state cuando corresponda
→ devuelve evidencia compacta.

No me pidas aprobación por:
- crear/rutear una Task;
- elegir detalles técnicos equivalentes;
- crear branches/worktrees/previews temporales dentro de autoridad;
- debugging;
- agregar pruebas;
- safe retry sin side effects materiales;
- continuar subfases obvias del mismo outcome.

Si para continuar necesitas:
- cambiar propósito o roadmap;
- crear/redefinir topología durable;
- introducir un nuevo repositorio/servicio/datastore/componente canónico;
- cambiar Protected Invariants;
- cruzar una Protected Boundary no autorizada;
- aceptar un riesgo/coste/dato/autoridad material nuevo;
- tomar una decisión de arquitectura o producto no resuelta;

no improvises.

Devuelve:
NEEDS_GOVERNANCE
Decision: [decisión material concreta]
Evidence: [mínimo necesario]
Options: [opciones reales, si existen]
Recommended: [recomendación, si existe]

Workspace Governance:
- distingue durable topology de ephemeral execution surface;
- puedes crear superficies efímeras dentro de autoridad sin límite arbitrario por cantidad;
- no conviertas una superficie temporal en componente durable por conveniencia;
- mantén lifecycle y cleanup seguro;
- si existe PROJECT.md, úsalo como mapa del workspace, no como backlog.

Continuidad:
- no dejes el proyecto dependiente de esta conversación;
- mantén implementación, Operational Baseline y hot project state dentro de autoridad;
- no inventes roadmap nuevo;
- si el cambio acumulado es estructural, aplica Memory Stewardship y ROUTE_TO_90 cuando corresponda.

No necesito que generes una Execution Task física si el Effective Execution Contract es suficientemente claro para esta ejecución.
```

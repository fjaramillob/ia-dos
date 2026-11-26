# Direct Execution y Workspace Governance

IA-DOS admite dos modos de entrada de primera clase para ejecutar trabajo:

```text
Execution Entry Mode:
ORCHESTRATED | DIRECT
```

No son niveles de calidad. Cambia quién materializa el contrato de ejecución, no las fronteras de autoridad.

## ORCHESTRATED

```text
persona responsable
→ Conversation Space / Cycle Owner
→ Execution Contract explícito
→ Coding Agent
```

Úsalo cuando aporte gobierno adicional: estrategia, roadmap, arquitectura, coordinación cross-domain, alternativas materiales, riesgo o ambigüedad que convenga resolver antes de ejecutar.

## DIRECT

```text
persona responsable
→ Coding Agent
→ rehidrata contexto durable
→ reconstruye Effective Execution Contract
→ ejecuta si Direct Execution Gate = PASS
```

El Conversation Space no es gateway obligatorio.

Direct Execution no elimina gobierno humano ni autoriza al Coding Agent a inventar dirección, roadmap, arquitectura o fronteras.

## Effective Execution Contract

En modo DIRECT no es obligatorio crear una `Execution Task` física antes de comenzar si la autoridad puede reconstruirse sin ambigüedad desde fuentes durables y la instrucción humana actual.

```text
Effective Execution Contract
=
Human Instruction
+ repository / AGENTS contracts
+ relevant current-state / durable decisions
+ actual repository and environment state
```

Debe permitir identificar como mínimo:

- outcome;
- Protected Invariants;
- Protected Boundaries;
- Authority Envelope efectivo;
- criterios de aceptación;
- stop conditions;
- Memory Policy / Stewardship cuando aplique.

Una `Execution Task` sigue siendo la materialización preferida cuando el contrato necesita viajar entre agentes, persistir durante una ejecución extensa, cruzar un handoff o hacer explícita autoridad sensible.

## Direct Execution Gate

Antes de escribir en DIRECT, el Coding Agent evalúa:

```text
1. ¿El outcome solicitado es suficientemente claro?
2. ¿Puedo reconstruir Protected Invariants desde fuentes autorizadas?
3. ¿Puedo identificar las Protected Boundaries que no debo cruzar?
4. ¿La autoridad necesaria está explícita o claramente delegada?
5. ¿Puedo verificar el resultado con evidencia objetiva?
6. ¿La memoria durable disponible evita depender de contexto conversacional indispensable ausente?
```

Resultados:

```text
PASS
→ self-plan
→ execute

NEEDS_GOVERNANCE
→ no improvisar dirección
→ devolver Decision Request compacto
→ persona responsable o Conversation Space
```

No conviertas una duda técnica ordinaria en `NEEDS_GOVERNANCE`. Con `Adaptation Authority: BOUNDED`, debugging, repair, tests adicionales y mecanismos equivalentes siguen dentro de ejecución.

## Agent self-planning

En DIRECT, self-planning es el default.

El Coding Agent puede:

- inspeccionar;
- derivar el plan técnico;
- implementar;
- probar;
- diagnosticar;
- reparar;
- realizar safe retry;
- usar Git/delivery dentro de autoridad;
- actualizar Operational Baseline y memoria LOCAL autorizada.

No necesita pedir que un Conversation Space traduzca cada intención humana en una Task.

## Governance Re-entry Trigger

El Conversation Space vuelve a ser útil cuando aparece una decisión de gobierno, no porque terminó una ejecución.

Reentra cuando, por ejemplo:

- cambia propósito o dirección;
- un milestone/capability material requiere reevaluar roadmap;
- aparece una alternativa arquitectónica material;
- cambia una Protected Boundary;
- surge nuevo riesgo, coste, dato, identidad o autoridad relevante;
- múltiples outcomes acumulados abren una decisión estratégica;
- el siguiente trabajo ya no puede inferirse del roadmap/dirección aceptados.

El trigger es semántico. No depende de número de commits, PR, Tasks, días o sesiones.

## Agent-Owned Continuity

En DIRECT, el Coding Agent debe dejar continuidad suficiente para que el proyecto no dependa de su conversación.

Dentro de autoridad, mantiene:

```text
implementation state
+ Operational Baseline
+ hot project state
```

No decide roadmap nuevo. Sí actualiza el estado de lo que ya quedó materializado y aceptado.

Si el cambio acumulado es estructural, aplica Memory Stewardship y `ROUTE_TO_90` cuando corresponda.

## Workspace Governance

IA-DOS distingue dos planos físicos.

### Durable topology

Recursos cuya existencia define la arquitectura o estructura permanente del proyecto, por ejemplo:

- repositorios canónicos;
- servicios durables;
- datastores;
- memoria durable;
- dominios o componentes top-level;
- integraciones permanentes;
- repositorios de infraestructura.

Crear, eliminar, fusionar o redefinir una superficie durable puede ser una decisión material.

### Ephemeral execution surface

Recursos temporales usados para producir un outcome, por ejemplo:

- Git branches;
- worktrees;
- previews;
- fixtures;
- scratch scripts;
- temporary environments;
- evidence directories;
- test databases cuando su lifecycle es explícitamente temporal.

El Coding Agent puede expandir esta superficie dentro de autoridad sin pedir aprobación por cantidad.

```text
autonomía alta
→ ephemeral execution

gobierno explícito
→ durable topology
```

IA-DOS no impone un máximo de branches, worktrees, agentes o previews. Impone claridad de lifecycle y separación de superficies.

## Workspace Hygiene Invariant

La raíz o punto de entrada de un proyecto debe permitir distinguir rápidamente:

- propósito;
- recursos canónicos;
- memoria durable;
- superficies operativas opcionales;
- ejecución efímera;
- archivo/cold storage.

Cuando la topología física es compleja, puede existir un `PROJECT.md` o mapa equivalente usando `templates/project-map.template.md`.

Ese mapa:

- no es backlog;
- no es Wiki;
- no es Artifact Type;
- no duplica documentación de arquitectura;
- orienta a humanos y agentes hacia las fuentes canónicas.

## Lifecycle efímero

Los recursos temporales deben tener cierre.

```text
ACTIVE
→ puede permanecer

MERGED / COMPLETED
→ verificar estado
→ retirar superficie efímera cuando sea seguro

ABANDONED
→ preservar evidencia durable necesaria
→ retirar superficie efímera cuando sea seguro
```

No muevas worktrees manualmente sin comprender el mecanismo Git correspondiente. Usa operaciones compatibles con la herramienta y preserva trabajo no incorporado.

## Regla principal

> IA-DOS no controla cuánto puede trabajar el agente; controla qué partes del proyecto puede redefinir mientras trabaja.

El agente puede trabajar extensamente dentro de una frontera estable. Propósito, topología durable, dirección y fronteras materiales continúan bajo gobierno explícito.

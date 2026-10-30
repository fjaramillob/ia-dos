# Custodia de memoria estructural

IA-DOS distingue entre producir un cambio técnico y custodiar la representación durable del proyecto.

Cuando un proyecto adopta `90 — Documentación y memoria`, ese Conversation Space actúa como **custodio de memoria estructural**. No es dispatcher obligatorio, no aprueba ejecución técnica y no recibe cada outcome.

## Principio

```text
Conversation Space de dominio
→ gobierna el outcome técnico o funcional

90 — Documentación y memoria
→ gobierna síntesis, ubicación y coherencia de memoria estructural

Coding Agent
→ materializa la actualización documental cuando recibe autoridad
```

La separación preserva agnosticismo: la memoria durable describe el proyecto y sus contratos, no la perspectiva accidental del último espacio que desarrolló una pieza.

## Memory Stewardship

Las Tasks pueden declarar:

```text
Memory Stewardship:
LOCAL | 90_STRUCTURAL | NO APLICA
```

### `LOCAL`

El Cycle Owner puede definir y materializar dentro del mismo outcome:

- Operational Baseline;
- release history compacta;
- memoria semántica estrecha y claramente local al dominio;
- correcciones documentales menores;
- hechos que no cambian la estructura conceptual del proyecto.

No exige Specialist Handoff a `90`.

### `90_STRUCTURAL`

El Cycle Owner conserva el gobierno del outcome, pero la síntesis durable estructural se deriva a `90 — Documentación y memoria` mediante `Specialist Handoff` inline.

Triggers típicos:

- arquitectura o topología relevante;
- modelo de datos o source of truth;
- contrato cross-domain;
- seguridad, autorización o modelo de identidad;
- lifecycle o gobernanza;
- capacidad mayor que redefine el estado vigente;
- cambio de frontera entre productos o sistemas;
- reorientación material de roadmap o estado;
- decisión que varios Conversation Spaces necesitarán reutilizar;
- reorganización relevante de la propia memoria/Wiki.

No uses un umbral mecánico de tamaño, cantidad de archivos o número de Tasks.

## Qué normalmente no requiere 90

Por sí solos no justifican routing estructural:

- bugfix local;
- ajuste visual o microcopy;
- refactor interno sin cambio contractual;
- tests adicionales;
- cambio de runner o herramienta equivalente;
- Preview o deployment ID ordinario;
- detalle de implementación fácil de redescubrir;
- resultado operativo transitorio.

Si alguno de ellos revela una decisión estructural, entonces sí activa `90_STRUCTURAL`.

## Flujo estructural

Después de que el outcome técnico quede suficientemente verificado:

```text
Cycle Owner
→ identifica Durable Memory Impact = ROUTE_TO_90
→ Specialist Handoff inline a 90
→ 90 revisa evidencia y memoria vigente
→ decide:
   NO UPDATE
   | CONSOLIDATE
   | MATERIALIZE NOW
→ si hay escritura:
   Wiki Update Task / Execution Task
→ Coding Agent
→ Execution Report
→ 90 revisa coherencia durable
```

`90` puede consolidar varios outcomes estructurales relacionados en una sola actualización cuando eso produzca una representación más limpia.

No se requiere volver a `00` salvo reorientación real.

## Bootstrap estructural

Si conocimiento estructural indispensable vive sólo en conversaciones y una futura unidad depende de él:

```text
Memory Bootstrap Gate = BOOTSTRAP REQUIRED
→ Specialist Handoff a 90 cuando el proyecto adopta ese rol
→ 90 define el checkpoint durable mínimo
→ Wiki Update Task
→ revisión
→ reevaluar el gate original
```

Un bootstrap local y no estructural puede seguir siendo gobernado por el Cycle Owner cuando no requiere custodia especializada.

## Operational Baseline

El Operational Baseline no se considera estructural por defecto.

Una Execution Task de BUILD/FIX/RELEASE puede actualizarlo dentro del mismo Authority Envelope cuando cambia el estado publicado. Esto evita convertir a `90` en peaje de cada deploy.

Si la publicación también cambia arquitectura, seguridad, datos, contratos cross-domain u otra dimensión estructural, el baseline puede actualizarse localmente y la síntesis semántica se deriva después a `90`.

## Durable Memory Impact

El Execution Report puede declarar:

```text
Durable Memory Impact:
NONE
| UPDATED
| DEFERRED
| ROUTE_TO_90
| ATTENTION REQUIRED
```

- `NONE`: no existe impacto durable;
- `UPDATED`: memoria autorizada quedó materializada, incluida memoria estructural cuando la Wiki Update Task ya fue gobernada por `90`;
- `DEFERRED`: outcome menor que puede consolidarse más adelante;
- `ROUTE_TO_90`: existe impacto estructural todavía pendiente de custodia especializada;
- `ATTENTION REQUIRED`: contradicción, ambigüedad o decisión de memoria que requiere gobierno antes de persistir.

`ROUTE_TO_90` no significa que la ejecución técnica esté incompleta. Una vez que `90` recibe el handoff y gobierna una Wiki Update Task, esa ejecución documental reporta `UPDATED` si la materialización termina correctamente; no genera un nuevo `ROUTE_TO_90`.

## Cumulative Memory Trigger

`DEFERRED` describe correctamente un outcome individual que todavía no justifica una actualización semántica. No es permiso para acumular indefinidamente deltas que ya cambian la comprensión del proyecto.

Reevalúa consolidación cuando varios outcomes, considerados en conjunto, cambian uno o más de estos elementos:

- estado vigente;
- outcome activo;
- capability o milestone aceptado;
- blocker o decisión material pendiente;
- próximo horizonte ya aceptado;
- arquitectura, autoridad, datos o contrato reusable;
- Operational Baseline o relación relevante entre implementación y publicación.

No existe umbral por número de Tasks, días, archivos o reportes. El trigger es **semántico**: si un agente nuevo recibiría una imagen materialmente equivocada o incompleta leyendo la memoria vigente, corresponde consolidar.

Cuando el cambio acumulado es estructural y el proyecto adopta `90`, usa `ROUTE_TO_90`. Cuando es estrecho y local, puede consolidarse bajo `LOCAL` si existe autoridad.

## Project State Continuity Invariant

Cuando un proyecto adopta memoria durable, debe existir una superficie caliente —`status/current-state.md` en el starter o equivalente— desde la cual un Conversation Space o agente competente pueda reconstruir con lectura acotada:

- qué es verdad ahora;
- qué outcomes están activos;
- qué capabilities/milestones relevantes están aceptados;
- qué blockers o decisiones materiales siguen abiertos;
- cuáles son los próximos horizontes ya aceptados, si existe roadmap;
- cuál es el Operational Baseline vigente cuando aplique;
- dónde profundizar para detalle de dominio.

Esta superficie no inventa roadmap ni selecciona prioridades nuevas. Sólo representa dirección y estado ya aceptados.

## Higiene de Wiki

La memoria caliente debe optimizar incorporación de agentes, no acumulación histórica.

Un patrón preferente:

```text
home / mapa
→ current-state compacto
→ página de dominio relevante
→ Task vigente
```

`current-state` debe actuar como índice operativo y snapshot vigente. Cuando crece por acumulación cronológica o mezcla demasiados dominios:

- conserva en él sólo estado vigente y navegación;
- mueve detalle reusable a páginas de dominio;
- mueve historia sólo cuando aporte continuidad;
- evita copiar TASK/REPORT, matrices completas, hashes repetidos y logs;
- deja a Git, delivery y Execution Reports conservar evidencia exhaustiva.

La necesidad de reorganizar memoria por pérdida de navegabilidad es un trigger estructural para `90`.

## Exchange y memoria

Exchange permanece operacional y pasivo.

```text
inbox/outbox
→ artifacts activos o todavía necesarios

archive
→ cold storage operacional

LLM Wiki
→ conocimiento durable vigente
```

Mantén la superficie activa escasa. Retira duplicados y artifacts superseded cuando ya no sean necesarios para trabajo activo, sin usar la carpeta como fuente de estado o aprobación.

## Regla final

```text
No todo cambio durable requiere 90.
Todo cambio durable estructural merece una mirada agnóstica del desarrollo.
```

# Actualización de la memoria durable

Cuando un proyecto utiliza una LLM Wiki, IA-DOS la trata como memoria durable de alta señal: conocimiento vigente para humanos y agentes, no como diario de ejecución.

La Wiki debe permitir que un Coding Agent competente se incorpore en cualquier punto del desarrollo usando:

```text
repositorio real
+ Wiki relevante
+ Execution Task vigente
→ comprensión suficiente para contribuir
→ revalidación del estado real antes de modificar
```

La implementación, Git y producción siguen siendo autoridad para demostrar qué existe realmente. La Wiki conserva comprensión durable y el último baseline operacional verificado.

## Dos responsabilidades distintas

### Memoria semántica

Conserva aquello que cambia cómo debe entenderse o desarrollarse el proyecto:

- capacidades relevantes;
- contratos funcionales;
- arquitectura;
- modelos de datos;
- seguridad y autoridad;
- fuentes de verdad;
- decisiones durables;
- restricciones;
- estado significativo del roadmap.

No todo outcome merece una actualización semántica.

La Execution Task declara:

```text
Memory Policy: NONE | CONDITIONAL | REQUIRED
Memory Stewardship: LOCAL | 90_STRUCTURAL | NO APLICA
```

- `NONE`: no corresponde cambio semántico de Wiki;
- `CONDITIONAL`: actualiza sólo si ocurre uno de los `Memory Triggers` explícitos;
- `REQUIRED`: la actualización durable forma parte confirmada del outcome.

Varios outcomes menores pueden quedar `DEFERRED` y consolidarse más adelante cuando juntos formen un cambio durable.

`Memory Stewardship` separa memoria local de memoria estructural:

- `LOCAL`: Operational Baseline y memoria semántica estrecha pueden quedar dentro del mismo outcome;
- `90_STRUCTURAL`: arquitectura, datos/source of truth, seguridad/autoridad, contratos cross-domain, capacidades mayores, gobernanza o reorganización relevante de la memoria se derivan a `90 — Documentación y memoria` cuando el proyecto adopta ese custodio.

### Operational Baseline

En un proyecto con LLM Wiki, todo cambio de estado publicado debe dejar actualizado el baseline operacional durable aunque `Memory Policy = NONE`.

Debe permitir identificar, cuando aplique:

- repositorio de implementación;
- branch productiva;
- último HEAD remoto verificado;
- commit o versión realmente publicada;
- deployment, release o identificador equivalente;
- entorno y URL/endpoint canónico;
- estado observado;
- fecha de verificación.

```text
Repository HEAD
puede ser distinto de
Production Commit
```

Esa diferencia debe ser visible.

El Operational Baseline es un checkpoint para continuidad. No autoriza a confiar ciegamente en él: el siguiente Coding Agent debe revalidar remoto, worktree, runtime y producción antes de escribir.

No registres dentro de la propia Wiki un `Wiki HEAD` autorreferente que obligue a otro commit sólo para almacenar su SHA. El HEAD actual de la Wiki se obtiene desde su repositorio.

## Historial de publicación

Cuando el proyecto tiene releases o deployments, la Wiki puede mantener un historial compacto de baselines publicados significativos.

Cada entrada debe ser proporcional, por ejemplo:

```text
Fecha / outcome
App commit
Production commit
Deployment o release
Estado
Verificación relevante
```

No copies cada commit, cada Task, cada Report ni cada deployment intermedio. Git y la plataforma de delivery conservan el historial exhaustivo.

Si el proyecto ya tiene una página equivalente, reutilízala. No impongas `status/release-history.md` por nombre.

## Gobierno

```text
Persona responsable
→ conserva criterio y dirección

Project Orchestrator / Cycle Owner
→ define qué outcome perseguir
→ define Memory Policy y Memory Stewardship
→ define Memory Triggers cuando corresponda
→ define si el baseline publicado debe actualizarse
→ deriva a 90 cuando el impacto durable es estructural
→ decide cuándo consolidar varios outcomes

90 — Documentación y memoria, cuando el proyecto lo adopta
→ custodia síntesis, ubicación y coherencia de memoria estructural
→ decide NO UPDATE | CONSOLIDATE | MATERIALIZE NOW

Coding Agent — Execution
→ materializa sólo dentro de la Task y Authority Envelope
→ actualiza memoria LOCAL si la política y los triggers lo habilitan
→ actualiza Operational Baseline cuando cambia publicación y está autorizado
→ ante 90_STRUCTURAL reporta ROUTE_TO_90
→ reporta evidencia
```

La capacidad de actualizar memoria no transfiere al Coding Agent autoridad para decidir roadmap, prioridades, producto o arquitectura fuera de la frontera delegada.

## Actualización dentro del mismo outcome

Cuando implementación, Git, delivery y memoria `LOCAL` comparten una frontera estable de autoridad, la actualización durable puede ocurrir dentro de la misma Execution Task.

No uses esta regla para absorber memoria estructural en el Conversation Space que desarrolló el cambio cuando la Task declara `90_STRUCTURAL`.

Ejemplo:

```text
Revalidate
→ Implement
→ Verify
→ Commit
→ Push
→ Deploy
→ Production Smoke
→ Semantic Memory LOCAL, si Memory Policy lo exige
→ Operational Baseline, si cambió publicación
→ Execution Report
```

No abras una Task de Wiki sólo porque terminó una ejecución.

## Cuándo sí usar una Wiki Update Task separada

Usa una Execution Task documental separada cuando el resultado principal sea:

- materializar un checkpoint por `Memory Bootstrap Gate = BOOTSTRAP REQUIRED`;
- consolidar varios outcomes menores en una síntesis durable;
- reparar contradicciones u obsolescencia de la memoria;
- migrar o reorganizar estructura documental;
- custodiar memoria estructural derivada a `90`;
- actualizar memoria bajo una frontera de autoridad distinta de la ejecución original.

El perfil [Wiki Update Task](../../templates/wiki-update-task.template.md) sigue siendo una Execution Task canónica; no es un Artifact Type nuevo.

## Entrada mínima para una actualización autorizada

La Task debe indicar:

- `Memory Policy`;
- `Memory Stewardship`;
- `Memory Triggers` cuando sea `CONDITIONAL`;
- regla de `Operational Baseline`;
- conocimiento confirmado que puede persistirse;
- fuentes de autoridad;
- Required Reading;
- rutas modificables y prohibidas;
- contenido que debe preservarse;
- Authority Envelope para Wiki/Git;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

No envíes la historia completa del proyecto.

## Conducta del Coding Agent

Debe:

1. confirmar recurso, branch y rutas autorizadas;
2. leer instrucciones locales y sólo el Required Reading;
3. inspeccionar memoria y fuentes reales antes de escribir;
4. preservar conocimiento vigente fuera de alcance;
5. no inventar decisiones ni completar vacíos por simetría;
6. distinguir implementado, decidido/no implementado, pendiente, fuera de alcance y desconocido;
7. mantener Markdown portable y enlaces relativos;
8. actualizar semantic memory sólo conforme a la política de la Task;
9. actualizar el Operational Baseline cuando el outcome cambie publicación y esa autoridad esté incluida;
10. revisar el diff y validar navegación;
11. devolver un Execution Report evidence-first.

Si aparece una decisión nueva de dirección, producto, arquitectura, seguridad, datos o riesgo fuera de la autoridad recibida, debe detenerse.

## Resultado en Execution Report

El Report debe indicar de forma compacta:

```text
Durable Memory Impact:
NONE | UPDATED | DEFERRED | ROUTE_TO_90 | ATTENTION REQUIRED

Operational Baseline:
UNCHANGED | UPDATED | NO APLICA | BLOQUEADO
```

- `NONE`: no hubo impacto semántico durable;
- `UPDATED`: la memoria LOCAL autorizada fue actualizada;
- `DEFERRED`: el cambio individual no justificó consolidación todavía;
- `ROUTE_TO_90`: el cambio durable es estructural y corresponde Specialist Handoff a `90`; no implica que el outcome técnico esté incompleto;
- `ATTENTION REQUIRED`: existe una decisión o contradicción que requiere gobierno.

Si un outcome publicó una nueva versión y la Task exigía actualizar el Operational Baseline pero no pudo hacerlo, no debe declararse completamente cerrado sin explicar la limitación.

## Higiene de current-state

Mantén el camino caliente de memoria corto:

```text
home / mapa
→ current-state compacto
→ página de dominio relevante
→ Task vigente
```

`current-state` describe principalmente qué es verdad ahora y dónde encontrar detalle reusable. No debe acumular cada checkpoint, hash, test matrix o cronología. Cuando deja de ser navegable, su reorganización es trabajo estructural de `90` cuando ese rol está adoptado.

## Validaciones mínimas

Verifica según corresponda:

- Markdown legible;
- enlaces relativos afectados;
- YAML válido cuando exista;
- navegación desde el home;
- ausencia de secretos;
- separación de estados;
- preservación fuera de alcance;
- baseline operacional coherente con evidencia real;
- diff limitado a rutas autorizadas;
- historial de publicación compacto, sin duplicar Git.

## Regla principal

```text
Orchestrator gobierna dirección y memoria
Coding Agent materializa dentro de autoridad
Wiki conserva comprensión durable + continuidad operacional
Repository y Production demuestran realidad técnica
Execution Report conserva evidencia del outcome
```

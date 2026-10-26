# Ejecución adaptativa y fronteras protegidas

IA-DOS gobierna resultados, invariantes y fronteras de riesgo. El Coding Agent gobierna los medios técnicos dentro de la autoridad explícitamente delegada.

## Principio

```text
Outcome
+ Protected Invariants
+ Authority Envelope
+ Adaptation Authority
+ Protected Boundaries
+ Acceptance
= contrato de ejecución
```

Una Execution Task no debe congelar por defecto la receta exacta de comandos, herramientas o microdecisiones cuando varias alternativas técnicamente equivalentes pueden alcanzar el mismo resultado sin cambiar la frontera material.

## Adaptation Authority

La Task declara:

```text
Adaptation Authority: NONE | BOUNDED
```

### `NONE`

Usa `NONE` cuando el mecanismo exacto forma parte del contrato: evidencia frozen, procedimiento regulado, migración byte-exact, secuencia de recovery aprobada u otra situación donde variar el medio cambia el riesgo o la interpretación del resultado.

### `BOUNDED`

Autoriza al Coding Agent a resolver defectos técnicos dentro del outcome y de los invariantes declarados.

Puede, cuando la capacidad correspondiente ya esté autorizada:

- inspeccionar y diagnosticar;
- elegir entre mecanismos técnicamente equivalentes;
- reparar implementation defects dentro del scope;
- crear o ajustar pruebas necesarias para demostrar los mismos invariantes;
- repetir tests, builds y verificaciones;
- revalidar precondiciones;
- cambiar runner, comando o técnica equivalente sin cambiar la semántica autorizada;
- reintentar después de un intento fallido cuando exista evidencia suficiente de que no produjo side effects materiales;
- continuar hasta Final State sin volver al Conversation Space por cada iteración ordinaria.

No autoriza:

- cambiar outcome o criterios semánticos de aceptación;
- debilitar Protected Invariants;
- ampliar arquitectura, seguridad, datos, identidad, coste o scope;
- cruzar una Protected Boundary no autorizada;
- introducir un servicio externo, credencial o principal nuevo no cubierto;
- adaptar después de observar evidencia frozen cuando el protocolo prohíbe tuning;
- reintentar ciegamente después de un estado parcial o irreversible.

## Protected Invariants

Una Execution Task de mayor abstracción declara lo que no puede cambiar mientras el agente adapta el método.

Ejemplos:

- semántica de una migración;
- atomicidad y ausencia de estado parcial;
- least privilege;
- contrato funcional;
- schema o API que debe preservarse;
- aislamiento de red;
- identidad exacta del target;
- separación DEV/Preview/Production;
- corpus frozen y reglas anti-leakage;
- coste máximo;
- privacidad o datos que no pueden utilizarse.

Los invariantes deben ser pocos, verificables y materiales. No conviertas cada detalle de implementación en un invariante.

## Zonas de ejecución

### Zona A — Engineering reversible

Por defecto puede incluir, si la Task autoriza escritura local:

```text
inspect
→ internally plan
→ implement
→ test
→ diagnose
→ repair
→ retry safely
→ revalidate
```

Los fallos ordinarios de implementación se resuelven aquí sin nueva Task, Planning Task, Preflight o ida y vuelta humana.

### Zona B — Remoto reversible / no productivo

Puede incluir, cuando el Authority Envelope lo autoriza explícitamente:

- branch;
- commit;
- push normal;
- pull request;
- Preview o staging;
- smoke remoto;
- artifacts temporales o efímeros.

Un efecto no productivo conocido e inseparable del mecanismo autorizado —por ejemplo un Preview automático por push— debe declararse en la Task y no transformarse luego en un ciclo separado por rutina.

### Zona C — Protected Boundary

Trata como frontera material, según el proyecto:

- mutaciones de Production;
- schema o datos productivos;
- permisos, ACL, roles, identidades o secretos;
- datos reales de usuario;
- coste externo material;
- acciones externas difíciles de revertir;
- publicación/promoción irreversible;
- evidencia experimental frozen;
- cambios regulatorios o de cumplimiento.

Una Zona C puede quedar autorizada desde la misma Execution Task. Si está explícitamente cubierta y sus gates pasan, el Coding Agent puede cruzarla sin nueva aprobación rutinaria.

Si durante la ejecución aparece una frontera C nueva o cambia su significado, STOP.

## Repair-in-place

Regla principal:

> Si un fallo técnico no produjo un efecto irreversible, no cambió el outcome, no cambió los Protected Invariants y puede resolverse dentro del Authority Envelope y Adaptation Authority vigentes, el Coding Agent debe repararlo y continuar dentro de la misma Execution Task.

No uses `BLOQUEADO` como sustituto de debugging ordinario.

El Execution Report final registra únicamente las adaptaciones materiales que ayudan a verificar el outcome. No narra cada intento.

## Planning interno y Planning Task

Todo Coding Agent puede planificar internamente cómo alcanzar un outcome autorizado.

Usa una `Planning Task` separada sólo cuando exista una decisión material todavía no resuelta antes de escribir, por ejemplo:

- alternativas arquitectónicas con efectos diferentes;
- cambio de modelo de seguridad;
- schema o semántica de datos aún no definidos;
- blast radius desconocido que condiciona la autorización;
- trade-off de coste o dependencia externa;
- decisión de producto o contrato funcional que no corresponde al Coding Agent.

Un bug de implementación o elección entre mecanismos equivalentes no justifica por sí solo Planning separado.

## Revalidate y Environment Preflight

Toda Execution Task comienza revalidando las precondiciones indispensables que pueden haber cambiado.

```text
Execution Task
→ Revalidate
→ ejecutar si PASS
→ adaptar o STOP según autoridad
```

Usa un `Environment Preflight` separado sólo cuando el readiness deba conocerse antes de conceder una autoridad sensible, cuando la capacidad misma sea el resultado que se quiere evaluar, o cuando la inspección requiera un actor/entorno distinto.

No dupliques un Preflight reciente dentro de Gate 0 salvo las comprobaciones volátiles realmente necesarias.

## Execution Resume

`Execution Resume` sigue siendo válido para reanudar una Task después de una interrupción real, una acción externa, una decisión humana o una condición que no podía resolver el executor dentro de su autoridad.

No es obligatorio para cada reparación técnica interna. Con `Adaptation Authority: BOUNDED`, el agente puede iterar dentro de la misma ejecución mientras no haya cerrado el Report ni cambiado la frontera material.

## Contratos especializados reutilizables

Un especialista como `40 — Calidad, seguridad y cumplimiento` debe ratificar invariantes, threat model, criterios y límites cuando corresponda.

Una vez aceptado ese contrato:

- la implementación puede evolucionar para cumplirlo;
- corregir un bug sin cambiar los invariantes no requiere nueva revisión especializada por defecto;
- el especialista vuelve a intervenir cuando cambia un invariante, threat model, autoridad, dato protegido, riesgo o condición material.

```text
Specialist Contract
→ invariantes ratificados
→ engineering loop autónomo
→ evidencia de cumplimiento
→ nueva revisión sólo si cambia la frontera
```

## Regla final

```text
IA-DOS gobierna el qué, los límites y la evidencia.
El Coding Agent decide el cómo dentro de esos límites.
```

# Registro de tópicos conversacionales

Este registro gobierna cómo IA-DOS distribuye razonamiento, decisiones y contexto entre Conversation Spaces.

No define una secuencia obligatoria. Sirve para abrir únicamente el espacio que resuelve la brecha dominante y asignar quién gobernará el resultado.

## Regla de enrutamiento

```text
petición, hallazgo o bloqueo
→ identificar la decisión dominante
→ comprobar si el espacio actual puede resolverla
→ continuar allí o abrir un único espacio especializado
→ confirmar resultado y asignar Cycle Owner
→ aplicar gates de memoria/readiness cuando corresponda
→ planificar o ejecutar
→ revisar desde el destino declarado
→ escalar sólo ante reorientación real
```

Antes de abrir otra conversación, pregunta:

```text
¿La brecha pertenece realmente a otro dominio
y requiere contexto persistente propio?
```

Si no, continúa en el espacio actual.

## Propiedad del ciclo y responsabilidad

El espacio que confirma el resultado esperado se convierte en Cycle Owner mientras permanezca dentro de su dominio.

El Cycle Owner actúa dentro de autoridad delegada. La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

Todo handoff debe declarar, según corresponda:

- Cycle Owner;
- destino del Environment Readiness Report;
- destino del Implementation Plan;
- destino del Execution Report;
- espacio de escalamiento;
- estado del resultado.

## Tópicos base

### `00 — Dirección y orquestación`

**Propósito:** mantener objetivo, prioridad, límites, organización transversal y reorientación.

**Abrir o volver cuando:** existe cambio de dirección, conflicto entre dominios, ampliación importante de alcance, decisión humana estratégica o bloqueo fuera de autoridad.

**No usar para:** recibir rutinariamente planes/reportes o actuar como intermediario cuando otro espacio ya gobierna el ciclo.

### `10 — Producto y UX`

**Propósito:** definir usuario, comportamiento, reglas funcionales, flujo y experiencia.

**Abrir cuando:** falta precisar qué debe ocurrir para el usuario, cómo comienza/termina un flujo o qué comportamiento constituye éxito.

**Fuera de alcance:** elegir infraestructura o ejecutar cambios físicos desde el chat.

### `20 — Arquitectura y stack`

**Propósito:** resolver arquitectura, datos, integraciones, seguridad estructural, restricciones técnicas y convergencia entre sistemas.

**Abrir cuando:** existe una decisión técnica real, auditoría que interpretar, migración que diseñar o riesgo arquitectónico que impide ejecutar con seguridad.

**Fuera de alcance:** redefinir silenciosamente producto o ejecutar cambios físicos desde el chat.

**Como Cycle Owner:** puede preparar Planning, Preflight o Execution Task y revisar retornos dentro de autoridad delegada; obtiene aprobación humana cuando corresponda.

### `30 — Ejecución y desarrollo`

**Propósito:** gobernar una iniciativa compleja cuando el espacio que resolvió la definición no puede coordinar de forma segura varias unidades ejecutables.

**Abrir cuando:** existen dependencias delicadas, múltiples unidades o coordinación que requiere contexto persistente propio.

**No abrir cuando:** otro espacio ya puede gobernar la primera tarea o cuando sólo hace falta una Execution Cell del coding agent.

`30` es Conversation Space; no equivale a una Execution Cell.

### `40 — Calidad, seguridad y cumplimiento`

**Propósito:** tratar pruebas, seguridad, privacidad, accesibilidad, riesgos y cumplimiento que requieren contexto propio.

**Abrir cuando:** la validación o el riesgo es la decisión dominante, no sólo una verificación normal incluida en otra tarea.

### `50 — Operación y entrega`

**Propósito:** resolver entornos, despliegue, observabilidad, releases, continuidad y operación.

**Abrir cuando:** el problema dominante es operativo o requiere contexto persistente de entrega.

**No usar como:** dispatcher obligatorio de toda Execution Task.

### `90 — Wiki y memoria`

**Propósito:** sintetizar conocimiento durable, resolver contradicciones y gobernar memoria cuando ese trabajo merece contexto propio.

**Abrir cuando:** existen múltiples fuentes, contradicciones, reorganización importante o una síntesis durable que se beneficia de continuidad especializada.

**No abrir por rutina:** un Memory Bootstrap mínimo o una actualización documental concreta ya confirmada pueden ser gobernados por el Conversation Space actual.

La modificación física de una LLM Wiki sigue requiriendo una Execution Task documental autorizada cuando la herramienta conversacional no es el recurso escritor.

## Selección del espacio

| Pregunta dominante | Tópico |
|---|---|
| ¿Qué priorizamos, cambiamos o escalamos? | `00` |
| ¿Qué debe experimentar o hacer el usuario? | `10` |
| ¿Cómo debe estructurarse técnicamente? | `20` |
| ¿Cómo gobernamos varias unidades de ejecución? | `30` |
| ¿Cómo comprobamos o reducimos el riesgo? | `40` |
| ¿Cómo entregamos y operamos? | `50` |
| ¿Qué conocimiento debe consolidarse? | `90` |

## Gate de salida

Cada espacio evalúa en este orden:

```text
1. ¿El siguiente resultado está definido, es pequeño y verificable?
2. Si depende de historia, ¿la memoria necesaria ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿corresponde Planning?
```

- memoria necesaria sólo en chats → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección/diseño → `Planning Task`;
- unidad lista → `Execution Task`;
- falta decisión del mismo dominio → continúa sólo hasta resolverla;
- falta decisión de otro dominio → `Specialist Handoff`;
- decisión humana indispensable → deriva sólo esa decisión;
- reorientación → escala a `00`.

Cuando `Memory Bootstrap Gate = BOOTSTRAP REQUIRED`, la unidad evaluada queda bloqueada. El mismo Cycle Owner puede emitir una `Execution Task` separada cuyo único resultado sea persistir el checkpoint durable mínimo; esa tarea deja la unidad original fuera de alcance, devuelve su `Execution Report` y sólo después se reevalúa el gate original. No presentes la tarea de bootstrap como `PASS`.

## Contrato del Conversation Space

Todo espacio debe poder declarar:

- tópico y nombre;
- objetivo único;
- entradas mínimas;
- fuera de alcance;
- estado del resultado;
- Cycle Owner;
- destinos de preflight, plan y reporte cuando apliquen;
- espacio de escalamiento;
- condición de cierre;
- fronteras de autoridad humana relevantes.

Los números son identificadores estables, no etapas obligatorias.

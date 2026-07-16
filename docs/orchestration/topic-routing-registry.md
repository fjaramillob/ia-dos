# Registro de tópicos conversacionales

Este registro gobierna cómo IA-DOS distribuye razonamiento, decisiones y contexto entre Conversation Spaces.

No define una secuencia obligatoria de chats. Sirve para abrir únicamente el espacio que resuelve la brecha dominante del momento.

## Regla de enrutamiento

```text
petición, hallazgo o bloqueo
→ identificar la decisión dominante
→ comprobar si el espacio actual puede resolverla
→ continuar allí o abrir un único espacio especializado
→ producir una salida útil
→ ejecutar o escalar solo cuando corresponda
```

Antes de abrir otra conversación, pregunta:

```text
¿La brecha pertenece realmente a otro dominio y requiere contexto persistente propio?
```

Si la respuesta es no, continúa en el espacio actual. Si ya existe claridad suficiente, prepara directamente una `Execution Task`.

## Tópicos base

### `00 — Dirección y orquestación`

**Propósito:** mantener objetivo, prioridad, límites, organización transversal y reorientación.

**Recibe:** cambios de dirección, conflictos entre dominios, ampliaciones relevantes de alcance, decisiones humanas estratégicas y bloqueos que ningún espacio especializado puede resolver con seguridad.

**No abrir otro espacio cuando:** `00` ya puede formular una pregunta concreta o preparar una tarea verificable.

**Salidas:** decisión humana, handoff a un único espacio o `Execution Task`.

### `10 — Producto y UX`

**Propósito:** definir usuario, comportamiento, reglas funcionales, flujo y experiencia.

**Abrir cuando:** falta precisar qué debe ocurrir para el usuario, cómo comienza y termina un flujo o qué comportamiento constituye éxito.

**Fuera de alcance:** elegir infraestructura, implementar archivos o resolver operación técnica detallada.

**Salidas:** decisión funcional, flujo acotado o `Execution Task` lista para materialización.

### `20 — Arquitectura y stack`

**Propósito:** resolver arquitectura, datos, integraciones, seguridad estructural, restricciones técnicas y convergencia entre sistemas.

**Abrir cuando:** existe una decisión técnica real, una auditoría que interpretar, una migración que diseñar o un riesgo arquitectónico que impide ejecutar con seguridad.

**Fuera de alcance:** redefinir silenciosamente el producto o ejecutar cambios físicos.

**Salidas:** decisión técnica, recomendación con trade-offs o `Execution Task`.

### `30 — Ejecución y desarrollo`

**Propósito:** descomponer una iniciativa compleja en tareas ejecutables cuando el espacio que resolvió la definición no puede hacerlo de manera segura y breve.

**Abrir cuando:** hay varias dependencias técnicas, orden de implementación delicado o necesidad de coordinar varias `Execution Tasks`.

**No abrir cuando:** `10`, `20`, `40`, `50` o `90` ya pueden preparar directamente la tarea.

**Salidas:** una `Execution Task` prioritaria o una secuencia mínima claramente dependiente.

### `40 — Calidad, seguridad y cumplimiento`

**Propósito:** tratar pruebas, seguridad, privacidad, accesibilidad, riesgos y cumplimiento que requieren contexto propio.

**Abrir cuando:** la validación o el riesgo es el problema dominante, no solo una verificación normal dentro de otra tarea.

**Salidas:** estrategia de verificación, criterio de riesgo, decisión de cumplimiento o `Execution Task` de tipo `TEST` o `HARDEN`.

### `50 — Operación y entrega`

**Propósito:** resolver entornos, despliegue, observabilidad, releases, continuidad y operación.

**Abrir cuando:** el problema dominante ocurre después de construir o requiere decisiones operativas persistentes.

**Salidas:** decisión operativa o `Execution Task` de tipo `RELEASE` u `OPERATE`.

### `90 — Wiki y memoria`

**Propósito:** sintetizar conocimiento durable, resolver contradicciones y gobernar memoria compleja.

**Abrir cuando:** una actualización documental acotada ya no basta por existir múltiples fuentes, contradicciones o reorganización importante.

**No abrir cuando:** la Wiki puede actualizarse como consecuencia directa de una tarea de producto o implementación.

**Salidas:** decisión documental, `Wiki Update Task` o `Execution Task` de tipo `WIKI`.

## Selección del espacio

Usa la decisión dominante, no todas las materias presentes:

| Pregunta dominante | Tópico |
|---|---|
| ¿Qué priorizamos o quién decide? | `00` |
| ¿Qué debe experimentar o hacer el usuario? | `10` |
| ¿Cómo debe estructurarse técnicamente? | `20` |
| ¿Cómo dividimos una ejecución compleja? | `30` |
| ¿Cómo comprobamos o reducimos el riesgo? | `40` |
| ¿Cómo entregamos y operamos? | `50` |
| ¿Qué conocimiento debe consolidarse? | `90` |

## Contrato de cada Conversation Space

Todo espacio especializado debe declarar:

- tópico y nombre;
- objetivo único;
- entradas mínimas;
- fuera de alcance;
- salida esperada;
- condición de cierre;
- espacio al que regresará una eventual ejecución.

Debe cerrar con una sola salida útil:

1. decisión humana pendiente;
2. handoff a otro espacio por una brecha nueva;
3. `Execution Task` lista para un coding agent;
4. actualización durable acotada.

Los números son identificadores estables, no etapas obligatorias. Un proyecto puede operar solo con `00` y abrir otros espacios únicamente cuando aporten separación real de contexto.
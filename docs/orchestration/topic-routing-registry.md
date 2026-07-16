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
→ planificar o ejecutar
→ revisar desde el destino declarado
→ escalar solo cuando corresponda
```

Antes de abrir otra conversación, pregunta:

```text
¿La brecha pertenece realmente a otro dominio
y requiere contexto persistente propio?
```

Si no, continúa en el espacio actual.

## Propiedad del ciclo

El espacio que confirma el resultado esperado se convierte en Cycle Owner mientras el resultado permanezca dentro de su dominio.

`00` también puede gobernar un ciclo.

Todo handoff debe declarar:

- Cycle Owner;
- destino del Implementation Plan, si existe;
- destino del Execution Report;
- espacio de escalamiento;
- estado del resultado.

No uses `Retorno` como único campo ambiguo.

## Tópicos base

### `00 — Dirección y orquestación`

**Propósito:** mantener objetivo, prioridad, límites, organización transversal y reorientación.

**Abrir o volver cuando:** existe cambio de dirección, conflicto entre dominios, ampliación importante de alcance, decisión humana estratégica o bloqueo fuera de la autoridad del espacio actual.

**No usar para:** volver a redactar tareas, recibir rutinariamente planes o reportes, ni actuar como intermediario cuando otro espacio ya gobierna el ciclo.

**Como Cycle Owner:** puede planificar, ejecutar y revisar resultados propios de dirección u orquestación.

### `10 — Producto y UX`

**Propósito:** definir usuario, comportamiento, reglas funcionales, flujo y experiencia.

**Abrir cuando:** falta precisar qué debe ocurrir para el usuario, cómo comienza y termina un flujo o qué comportamiento constituye éxito.

**Fuera de alcance:** elegir infraestructura o ejecutar cambios físicos desde el chat.

**Como Cycle Owner:** gobierna el resultado funcional hasta cerrarlo o transferir explícitamente su propiedad.

### `20 — Arquitectura y stack`

**Propósito:** resolver arquitectura, datos, integraciones, seguridad estructural, restricciones técnicas y convergencia entre sistemas.

**Abrir cuando:** existe una decisión técnica real, auditoría que interpretar, migración que diseñar o riesgo arquitectónico que impide ejecutar con seguridad.

**Fuera de alcance:** redefinir silenciosamente el producto o ejecutar cambios físicos desde el chat.

**Como Cycle Owner:** puede enviar una Planning Task, revisar el Implementation Plan, aprobar una Execution Task técnica y revisar su evidencia.

### `30 — Ejecución y desarrollo`

**Propósito:** coordinar una iniciativa compleja cuando el espacio que resolvió la definición no puede gobernar de forma segura su descomposición técnica.

**Abrir cuando:** existen dependencias delicadas, múltiples unidades ejecutables o coordinación que requiere contexto persistente propio.

**No abrir cuando:** otro espacio ya puede gobernar el plan y la primera tarea.

### `40 — Calidad, seguridad y cumplimiento`

**Propósito:** tratar pruebas, seguridad, privacidad, accesibilidad, riesgos y cumplimiento que requieren contexto propio.

**Abrir cuando:** la validación o el riesgo es el problema dominante, no solo una verificación normal dentro de otra tarea.

### `50 — Operación y entrega`

**Propósito:** resolver entornos, despliegue, observabilidad, releases, continuidad y operación.

**Abrir cuando:** el problema dominante ocurre después de construir o requiere decisiones operativas persistentes.

### `90 — Wiki y memoria`

**Propósito:** sintetizar conocimiento durable, resolver contradicciones y gobernar memoria compleja.

**Abrir cuando:** una actualización acotada ya no basta por existir múltiples fuentes, contradicciones o reorganización importante.

**No abrir cuando:** la memoria puede actualizarse como consecuencia directa de otra tarea.

## Selección del espacio

| Pregunta dominante | Tópico |
|---|---|
| ¿Qué priorizamos, cambiamos o escalamos? | `00` |
| ¿Qué debe experimentar o hacer el usuario? | `10` |
| ¿Cómo debe estructurarse técnicamente? | `20` |
| ¿Cómo coordinamos varias unidades de ejecución? | `30` |
| ¿Cómo comprobamos o reducimos el riesgo? | `40` |
| ¿Cómo entregamos y operamos? | `50` |
| ¿Qué conocimiento debe consolidarse? | `90` |

## Gate de salida

Cada espacio evalúa:

```text
¿El siguiente resultado puede ejecutarse directamente
o necesita primero inspección y planificación técnica?
```

- **Ejecución directa:** entrega una Execution Task pequeña y verificable.
- **Planificación previa:** entrega una Planning Task.
- **Falta una decisión del mismo dominio:** continúa solo hasta resolverla.
- **Falta una decisión de otro dominio:** deriva una sola vez.
- **Hace falta reorientación:** escala a `00`.

## Contrato del Conversation Space

Todo espacio debe declarar:

- tópico y nombre;
- objetivo único;
- entradas mínimas;
- fuera de alcance;
- estado del resultado;
- Cycle Owner;
- destinos de plan y reporte;
- espacio de escalamiento;
- condición de cierre.

Los números son identificadores estables, no etapas obligatorias.
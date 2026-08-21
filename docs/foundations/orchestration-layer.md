# Capa de orquestación conversacional

IA-DOS organiza la capa de conversación desde la que una persona dirige el proyecto y la conecta con planificación y ejecución técnica sin convertir chats o sesiones en fuentes de verdad paralelas.

Para muchos usuarios, especialmente quienes no son programadores expertos, esta capa será la interfaz principal del desarrollo.

## Qué es

La capa de orquestación conversacional puede implementarse como:

- un Project de ChatGPT;
- un Gem de Gemini;
- un Project de Claude;
- una conversación persistente;
- un asistente personalizado;
- otro entorno equivalente.

Su función es comprender el proyecto, ordenar contexto, separar conversaciones solo cuando aportan, registrar decisiones durables en la fuente adecuada y transformar necesidades en trabajo verificable para coding agents.

## Qué consume

El Project Orchestrator puede recibir:

1. IA-DOS, para conocer el método;
2. memoria durable del proyecto, cuando exista;
3. repositorios o artefactos de implementación cuando tenga acceso;
4. evidencia, reportes o referencias históricas;
5. instrucciones específicas del usuario o del equipo.

IA-DOS define cómo trabajar. El proyecto define qué fuentes tienen autoridad para cada ámbito.

## Qué produce

La capa conversacional puede producir:

- decisiones confirmadas;
- `Specialist Handoff`;
- `Planning Task`;
- `Environment Preflight`;
- `Execution Task`;
- criterios de aceptación;
- instrucciones para actualizar memoria durable;
- revisión de `Implementation Plan` y `Execution Report`;
- siguientes decisiones o escalamiento.

Una conversación no debe quedar como único lugar donde vive una decisión importante.

## Arquitectura

```text
Usuario
   ↓
Project Orchestrator / Conversation Space
   │
   ├── consulta método y fuentes autorizadas
   ├── confirma el siguiente resultado
   ├── actúa como Cycle Owner cuando corresponde
   └── prepara un artefacto tipado
            ↓
      Planning Task
            o
      Execution Task
            ↓
       coding agent
            ↓
Implementation Plan o Execution Report
            ↓
      mismo Cycle Owner
            ↓
revisión → cierre | corrección | transferencia | escalamiento
```

## Conversation Spaces

Un `Conversation Space` es una conversación persistente dedicada a un dominio de gobierno del proyecto.

La única lista normativa de tópicos y nombres vive en:

`docs/orchestration/topic-routing-registry.md`

No copies esa lista en otros documentos como si fuera una estructura paralela. Los espacios se abren bajo demanda cuando una brecha requiere autoridad o contexto persistente propio.

Un proyecto pequeño puede trabajar durante bastante tiempo en un solo espacio. Los números identifican dominios; no representan fases obligatorias.

## `00`

`00` orienta dirección, prioridad y reorientación. No debe convertirse en dispatcher obligatorio ni recibir planes y reportes rutinarios de otros Cycle Owners.

Cuando otro Conversation Space confirma un resultado dentro de su dominio, ese espacio puede gobernar el ciclo y recibir directamente los retornos correspondientes.

## Conversation Space ≠ Execution Cell

IA-DOS separa gobierno de continuidad de ejecución:

```text
Conversation Space
→ decide y gobierna

Execution Cell
→ conserva contexto durable de ejecución en el coding agent

Execution Task
→ delimita una unidad concreta y sus permisos
```

Una `Execution Cell` no representa una especialidad profesional ni una tarea. Cuando la herramienta ofrece conversaciones persistentes, puede mantenerse una sola conversación activa por célula mientras siga respondiendo bien.

No abras una conversación nueva del coding agent por cada Execution Task. Reutilizar una conversación tampoco reutiliza permisos: cada tarea vuelve a declarar alcance, autoridad y acciones autorizadas.

## Planificación técnica

Cuando falta inspección o diseño, el Conversation Space Cycle Owner prepara una `Planning Task` para `Coding Agent — Planning`.

La Planning Task:

- es de solo lectura;
- resuelve una incertidumbre técnica dominante;
- produce un `Implementation Plan`;
- no autoriza ejecución.

La política de persistencia de conversaciones de planificación se mantiene separada de la política de Execution Cells y no debe inferirse automáticamente.

## Entrada estructurada a ejecución

Una necesidad clara se convierte en un contrato de ejecución:

```text
necesidad o decisión confirmada
    ↓
Execution Task
    ↓
Execution Cell adecuada o entorno disponible
    ↓
Execution Report
```

Toda Execution Task sigue un único contrato semántico definido en `docs/orchestration/typed-artifact-routing.md`.

Exchange, cuando se utiliza, sólo transporta o conserva el archivo `.md` ya construido. La identidad de la tarea pertenece al Conversation Agent y al contrato del artefacto; Exchange no genera, modifica ni valida IDs.

## Optimización de contexto

El Orchestrator no debe reenviar la historia completa del proyecto en cada handoff.

La regla general es:

```text
fuente durable vigente
+
contexto mínimo seleccionado
+
delta de la tarea
+
contrato operativo explícito
```

Una Execution Task puede distinguir:

- `Contexto durable necesario`: hechos que deben viajar en la tarea;
- `Referencias Wiki`: trazabilidad o navegación, sin obligación de lectura;
- `Lectura requerida`: documentos concretos que el coding agent debe consumir.

Cuando una fuente durable no es accesible, el Orchestrator incluye solo el extracto indispensable. Permisos, alcance, criterios y condiciones de detención no se eliminan por compresión.

## Flujo de retorno

El coding agent devuelve el artefacto solicitado al Cycle Owner indicado.

Al revisar un `Execution Report`, el Orchestrator debe:

1. comparar objetivo versus resultado;
2. revisar evidencia y verificaciones;
3. comprobar alcance y autorizaciones;
4. identificar riesgos, desviaciones, pendientes del alcance original y cualquier atención requerida;
5. decidir cierre, corrección, reversión, escalamiento o siguiente unidad;
6. evaluar después si algún hecho nuevo merece consolidación en memoria durable.

El Execution Report aporta evidencia; no selecciona la decisión de gobierno posterior y no es memoria durable.

La afirmación del agente no reemplaza la evidencia.

## Regla de autoridad

- La conversación dirige, revisa y decide.
- La memoria durable conserva conocimiento vigente y confirmado.
- La implementación demuestra qué está materializado.
- La `Execution Task` conserva el alcance autorizado de una ejecución.
- El `Execution Report`, diff, revisión o PR conserva evidencia.
- Exchange, cuando existe, sólo transporta o conserva archivos intercambiados y no sustituye ninguna de las fuentes anteriores.

IA-DOS conecta estas capas para que una conversación se convierta en trabajo útil, acotado, trazable y reemplazable sin depender del historial de chats.
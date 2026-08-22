# Capa de orquestación conversacional

IA-DOS organiza la capa desde la que una persona dirige el proyecto y la conecta con planificación y ejecución técnica sin convertir chats o sesiones en fuentes de verdad paralelas.

## Qué es

La capa puede implementarse como Project, Gem, conversación persistente, asistente personalizado u otro entorno equivalente.

Su función es:

- comprender propósito y prioridad suficientes;
- seleccionar fuentes y contexto;
- separar conversaciones sólo cuando aportan;
- preservar memoria durable antes de depender de historia chat-only;
- comprobar readiness indispensable antes de autorizar escritura;
- transformar necesidades en Planning, Preflight o Execution según corresponda;
- revisar retornos;
- mantener responsabilidad humana explícita.

## Responsabilidad

```text
Persona responsable
→ define dirección, restricciones y autoridad
→ conserva aprobación final cuando corresponde

Project Orchestrator / Cycle Owner
→ gobierna dentro de autoridad delegada

Coding Agent — Planning
→ inspecciona y propone

Coding Agent — Execution
→ ejecuta lo autorizado y produce evidencia
```

El Cycle Owner no sustituye a la persona responsable.

## Qué consume

Puede recibir:

1. IA-DOS, para conocer el método;
2. memoria durable del proyecto, cuando exista;
3. repositorios o artefactos de implementación;
4. evidencia, reportes o referencias históricas;
5. instrucciones específicas de la persona o equipo.

Cada recurso declara qué ámbito gobierna. No existe una fuente universal.

## Qué produce

La capa conversacional puede producir:

- decisiones confirmadas;
- `Specialist Handoff` inline y copiable hacia otro Conversation Space;
- resultado `PASS` o `BOOTSTRAP REQUIRED` del Memory Bootstrap Gate;
- `Planning Task`;
- `Environment Preflight`;
- `Execution Task`;
- criterios de aceptación;
- actualización documental explícitamente autorizada;
- revisión de `Environment Readiness Report`, `Implementation Plan` y `Execution Report`;
- cierre, corrección, transferencia, escalamiento o siguiente unidad bajo la autoridad aplicable.

Una conversación no debe quedar como único lugar donde vive conocimiento indispensable que otra unidad deberá reutilizar.

## Arquitectura

```text
Persona responsable
   ↓
Project Orchestrator / Conversation Space
   ↓
resultado verificable + Cycle Owner
   ↓
Memory Bootstrap Gate, cuando depende de historia
   ↓
Environment Preflight, cuando readiness indispensable es desconocido
   ↓
Planning Task, cuando falta inspección/diseño
   o
Execution Task, cuando la unidad está lista
   ↓
coding agent
   ↓
retorno tipado
   ↓
mismo Cycle Owner
   ↓
revisión dentro de autoridad delegada
   ↓
aprobación humana cuando corresponda
```

No es una pipeline obligatoria: cada gate se usa únicamente cuando aplica.

## Conversation Spaces

Un `Conversation Space` es un contexto persistente dedicado a un dominio de gobierno.

La lista normativa vive en `docs/orchestration/topic-routing-registry.md`.

Los espacios se abren bajo demanda. Un proyecto pequeño puede permanecer bastante tiempo en `00`. Los números identifican dominios; no representan fases.

Cuando una brecha dominante pertenece a otro Conversation Space, la transferencia usa un `Specialist Handoff` **inline, autocontenido y copiable**:

```text
Conversation Space origen
→ Specialist Handoff inline
→ persona copia/pega
→ Conversation Space destino
```

No requieras para ese routing un archivo `.md`, Exchange, un path de `inbox/` ni `Manual Artifact Launcher`. Una copia documental puede existir sólo como auxiliar explícitamente solicitado o por una convención local separada; no sustituye ni condiciona la transferencia inline.

## `00`

`00 — Dirección y orquestación` es la entrada canónica. Mantiene dirección y recibe reorientaciones o escalamiento real.

No es un dispatcher obligatorio ni debe recibir planes o reportes rutinarios de otros Cycle Owners.

## Conversation Space ≠ Execution Cell

```text
Conversation Space
→ gobierno y decisión

Execution Cell
→ continuidad de ejecución en el coding agent

Execution Task
→ autoridad de una unidad concreta
```

Una Execution Cell no es una tarea, profesión o Conversation Space.

Mantén una conversación activa por célula mientras siga respondiendo bien. No abras una conversación nueva por cada Task y no renueves por edad, mensajes o cantidad de tareas.

Reutilizar una conversación no acumula permisos.

## Planning

Cuando falta inspección o diseño, el Cycle Owner prepara una `Planning Task` de solo lectura.

Produce `Implementation Plan` y no autoriza ejecución.

IA-DOS no impone una política universal de persistencia de conversaciones de Planning. Un nombre `PLAN — ...` puede ser un identificador lógico y no obliga a abrir una conversación nueva.

## Readiness

Cuando una futura Execution Task depende de una precondición indispensable no comprobada, usa `Environment Preflight`.

Produce:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

Sólo `LISTO PARA EJECUCIÓN` habilita considerar autorización de escritura.

## Entrada a ejecución

```text
resultado definido
+ memoria suficiente
+ entorno listo
+ autoridad aplicable
→ Execution Task
→ Execution Cell o entorno disponible
→ Execution Report
```

Toda Execution Task conserva un único contrato semántico independientemente de su transporte.

## Exchange

Exchange, cuando se utiliza, es una pasarela pasiva y opcional de archivos `.md` **para el intercambio de artefactos con Coding Agents**.

```text
Conversation Space → Conversation Space
→ Specialist Handoff inline y copiable
→ no usa Exchange por defecto

Conversation Space → Coding Agent
→ Planning Task | Environment Preflight | Execution Task | Execution Resume
→ puede usar chat o `.md`/Exchange según el contrato de entrega
```

Exchange puede almacenar o poner a disposición artefactos ya construidos hacia o desde Coding Agents. No enruta Conversation Spaces.

La identidad de la tarea pertenece al Conversation Agent y al contrato del artefacto. Exchange no genera, modifica o valida IDs, artefactos, estados, permisos, backlog, memoria, workflow o routing conversacional.

## Optimización de contexto

```text
fuentes de autoridad
+ artefacto previo válido
+ contexto durable necesario
+ delta actual
+ contrato operativo explícito
```

Una tarea puede distinguir:

- `Contexto durable necesario`;
- `Referencias Wiki`;
- `Lectura requerida`.

Cuando una fuente no es accesible, incluye sólo el extracto indispensable. Permisos, alcance, criterios y condiciones de detención permanecen explícitos.

## Flujo de retorno

Al revisar un Execution Report:

1. compara objetivo versus resultado;
2. revisa evidencia y verificaciones;
3. comprueba alcance y autorizaciones;
4. identifica riesgos, desviaciones, pendientes y atención requerida;
5. el Cycle Owner decide dentro de autoridad delegada;
6. la persona responsable aprueba cuando corresponde;
7. después se evalúa por separado si hechos nuevos merecen memoria durable.

El reporte aporta evidencia. No selecciona la decisión de gobierno posterior y no es memoria durable.

## Regla de autoridad

- la persona mantiene dirección y aprobación final aplicable;
- la conversación gobierna;
- la memoria durable conserva conocimiento vigente;
- la LLM Wiki es una posible materialización de esa memoria;
- la implementación demuestra qué está materializado;
- la Execution Task conserva la autoridad de una ejecución;
- el Execution Report conserva evidencia;
- Exchange sólo conserva o transporta archivos intercambiados con Coding Agents y no enruta Conversation Spaces.

# Adoptar un proyecto existente desde la capa conversacional

Este recorrido está pensado para un proyecto que ya tiene código, documentación, decisiones o usuarios, pero todavía no cuenta con un Project Orchestrator configurado según IA-DOS.

El objetivo inicial no es reorganizar ni modificar el proyecto. Primero se debe comprender su estado real y crear una memoria durable basada en evidencia.

## 1. Crear el Project Orchestrator

Crea un Project de ChatGPT, un Gem de Gemini, un Project de Claude o un espacio equivalente dedicado exclusivamente al proyecto.

Entrega como contexto:

- el repositorio IA-DOS o, como mínimo, `README.md`, `ORCHESTRATOR.md` y `docs/index.md`;
- el repositorio de aplicación, cuando la plataforma pueda conectarlo;
- documentación existente;
- enlaces, reportes o archivos relevantes;
- restricciones conocidas.

Cuando la plataforma permita instrucciones persistentes, puede aplicarse opcionalmente `templates/project-instructions.template.md`. Debe contener reglas estables, no tareas ni estado cambiante.

Si la plataforma no puede conectarse al repositorio de aplicación, entrega primero una descripción general y utiliza un coding agent para inspeccionar el código y devolver un reporte estructurado.

## 2. Primera conversación: `00 — Descubrimiento y adopción`

La primera conversación debe determinar:

- qué producto existe;
- para quién funciona;
- qué partes están implementadas;
- qué partes están incompletas;
- qué documentación existe;
- qué decisiones siguen vigentes;
- qué repositorios, servicios e integraciones participan;
- qué problemas o riesgos son conocidos;
- qué información no ha sido verificada;
- cuál es la prioridad actual.

El orquestador debe trabajar con una regla estricta:

> No describir como real algo que no haya sido confirmado por una fuente, el usuario o una inspección del repositorio.

## 3. Verificar si existe una LLM Wiki

El orquestador debe identificar uno de estos casos:

### Caso A — Existe una wiki usable

Debe revisar si está versionada, tiene un punto de entrada claro, representa el estado actual, distingue implementado, planificado y desconocido, contiene decisiones y fuentes, y puede ser utilizada por personas y agentes.

No debe reemplazarla automáticamente. Primero debe proponer ajustes.

### Caso B — Existe documentación dispersa

Debe identificar qué documentos pueden conservarse como fuentes y cuáles deben sintetizarse dentro de una wiki. No debe copiar todo sin criterio.

### Caso C — No existe una wiki

El orquestador debe crear o proponer:

```text
90 — Wiki y memoria
```

Esa conversación guiará la implementación de una LLM Wiki basada en evidencia del proyecto existente.

Consulta [Crear la LLM Wiki](bootstrap-llm-wiki.md).

## 4. Construir la wiki sin inventar historia

Para un proyecto existente, la wiki inicial debe construirse mediante:

- inspección del repositorio en modo lectura;
- revisión de README, configuración, dependencias y estructura;
- lectura de documentación existente;
- revisión de issues y pull requests relevantes cuando estén disponibles;
- conversación con la persona responsable;
- registro explícito de dudas y contradicciones.

Los documentos deben usar estados claros:

```text
Implementado
Parcialmente implementado
Planificado
Deprecado
Desconocido
```

Una ausencia de evidencia debe registrarse como desconocida, no completarse con una inferencia presentada como hecho.

## 5. Crear Conversation Spaces de forma progresiva

Una vez que existe contexto mínimo, no propongas una taxonomía completa por defecto.

El mínimo inicial es:

```text
00 — Dirección y orquestación
90 — Wiki y memoria
```

La conversación `00` comienza como `Descubrimiento y adopción` y, terminada esa etapa, pasa a operar como `Dirección y orquestación`.

Cuando comience el trabajo técnico, agrega:

```text
30 — Ejecución y desarrollo
```

Su función es preparar `Execution Tasks`, realizar handoffs y revisar resultados con evidencia.

Agrega conversaciones opcionales solo cuando exista actividad recurrente, mezcla de contexto, fuentes propias, varias tareas relacionadas o necesidad de revisión especializada. Ejemplos:

```text
10 — Producto y UX
20 — Arquitectura y datos
40 — QA y seguridad
```

También pueden existir espacios específicos como operaciones, cumplimiento o comercial. Las iniciativas temporales pueden mantenerse en `00` o `30` mientras no justifiquen una conversación propia.

Un proyecto pequeño puede mantenerse solo con `00`, `30` y `90`.

## 6. Conectar conversación, wiki y aplicación

El orquestador debe reconocer:

```text
IA-DOS
    define cómo trabajar

Project Orchestrator
    dirige y convierte conversaciones en trabajo

LLM Wiki
    conserva contexto, decisiones y estado

Repositorio de aplicación
    conserva la implementación
```

Cuando tenga acceso a la app, debe consultarla solo cuando sea necesario.

Cuando no tenga acceso, debe preparar instrucciones para que Codex, Claude Code, Antigravity u otro coding agent inspeccione y reporte.

## 7. Relación con coding agents

No existe una relación uno a uno entre Conversation Spaces y coding agents.

La unidad de ejecución es:

```text
1 Execution Task
→ 1 ejecución acotada del coding agent
→ 1 resultado verificable
→ 1 Execution Report
```

Un Conversation Space puede originar múltiples tareas. Las sesiones del coding agent ejecutan trabajo; no son memoria durable.

## 8. Primera tarea después de la adopción

La primera tarea no debería ser una gran refactorización.

Debe ser una tarea de bajo riesgo que permita validar el flujo IA-DOS, por ejemplo:

- documentar la arquitectura actual;
- corregir un bug acotado;
- añadir una prueba faltante;
- actualizar una funcionalidad pequeña;
- verificar una integración.

El orquestador prepara la `Execution Task`, el coding agent ejecuta y devuelve evidencia, y la wiki se actualiza si cambió el conocimiento durable.

## Resultado esperado

Al finalizar este recorrido deben existir:

- un Project Orchestrator dedicado;
- una comprensión inicial del estado real;
- una LLM Wiki creada o revisada;
- preguntas y contradicciones registradas;
- conversaciones mínimas definidas;
- una primera tarea acotada para validar el modelo operativo.
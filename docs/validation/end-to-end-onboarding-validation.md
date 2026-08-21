# Validación end-to-end de onboarding

Esta validación comprueba que los principales recorridos de adopción y continuidad de IA-DOS converjan al mismo modelo operativo después de la consolidación de contratos, memoria, Exchange y distribución offline.

## Objetivo

Validar que distintos puntos de entrada produzcan la misma semántica fundamental:

```text
Conversation Space
→ gobierna y decide

Memory Bootstrap Gate
→ evita dependencia de contexto chat-only

Planning Task
→ inspección/diseño de solo lectura cuando hace falta

Execution Task
→ unidad concreta con permisos explícitos

Execution Cell
→ continuidad de ejecución cuando el proyecto la adopta

Execution Report
→ evidencia de retorno al Cycle Owner

Exchange
→ pasarela pasiva opcional de archivos .md

Wiki / memoria durable
→ conocimiento vigente y reusable

Repositorio
→ implementación real
```

La validación no exige que todos los proyectos adopten Wiki, Exchange, Execution Cells, repositorios separados o workspace local.

## Criterio de aceptación global

Todos los recorridos deben converger en estas reglas:

- `00 — Dirección y orquestación` es el Conversation Space inicial canónico;
- `definición inicial` y `descubrimiento y adopción` son modos de entrada, no nombres alternativos de `00`;
- Conversation Spaces se abren bajo demanda;
- el espacio que confirma el resultado gobierna como Cycle Owner mientras siga dentro de su dominio;
- una tarea no implica una conversación nueva del coding agent;
- una Execution Cell puede reutilizarse entre tareas sin reutilizar permisos;
- Memory Bootstrap Gate sólo bloquea cuando la siguiente unidad depende de conocimiento relevante que vive únicamente en conversaciones;
- Wiki/memoria durable conserva estado vigente, no TASK/REPORT completos ni backlog por defecto;
- Exchange no define IDs, artefactos, estados, permisos, workflow o memoria;
- una Execution Task mantiene el mismo contrato independientemente de su transporte;
- Planning y ejecución permanecen separadas;
- Environment Preflight se utiliza cuando una precondición indispensable no está comprobada;
- sólo `LISTO PARA EJECUCIÓN` habilita aprobar o reanudar escritura;
- Execution Resume sólo reanuda la misma tarea si no cambian objetivo, alcance, autoridad, seguridad o arquitectura;
- cada retorno vuelve al Cycle Owner declarado;
- `00` recibe reorientación o escalamiento real, no retornos rutinarios.

## Escenario A — Proyecto nuevo con repositorio accesible

### Entrada simulada

- producto nuevo;
- asistente con navegación del repositorio IA-DOS;
- descripción inicial disponible;
- siguiente resultado todavía no necesariamente implementable.

### Recorrido esperado

```text
initializer canónico
→ 00 — Dirección y orquestación / definición inicial
→ capturar dirección suficiente
→ abrir sólo el Conversation Space que resuelva la brecha dominante, si hace falta
→ Memory Bootstrap Gate cuando la siguiente unidad dependa de historia conversacional
→ Execution Task directa o Planning Task
→ Cycle Owner revisa retorno
```

### Evidencia revisada

- `prompts/getting-started/initialize-project-orchestrator.md`;
- `docs/getting-started/new-project-from-conversation.md`;
- `docs/orchestration/topic-routing-registry.md`;
- `docs/foundations/memory-bootstrap-gate.md`.

### Resultado

`PASS`.

El recorrido no impone Wiki, Exchange, workspace, stack ni conversaciones adicionales por rutina.

## Escenario B — Proyecto nuevo sin navegación del repositorio

### Entrada simulada

- producto nuevo;
- asistente sin navegación de GitHub;
- acceso al Current Offline Pack.

### Recorrido esperado

```text
bundles/ia-dos-current-offline-pack.md
→ validar Estado: VIGENTE + baseline
→ 00 — Dirección y orquestación / definición inicial
→ mismos gates, roles y artefactos del repositorio canónico
```

Si el pack vigente no está disponible:

```text
ORCHESTRATOR.md
+
templates/project-instructions.template.md
```

### Evidencia revisada

- `bundles/ia-dos-current-offline-pack.md`;
- `bundles/README.md`;
- `ORCHESTRATOR.md`;
- `README.md`;
- `docs/index.md`.

### Resultado

`PASS` después de Fase 5.

El pack vigente reproduce Memory Bootstrap Gate, Execution Cells, Environment Preflight, Execution Resume seguro, contrato único de Execution Task y Exchange pasivo. Los bundles anteriores están marcados como históricos antes de sus instrucciones antiguas.

## Escenario C — Proyecto existente sin Wiki

### Entrada simulada

- producto con implementación real;
- repositorio o fuentes técnicas disponibles;
- no existe Wiki estructurada;
- existe una siguiente unidad concreta.

### Recorrido esperado

```text
00 — Dirección y orquestación / descubrimiento y adopción
→ inspeccionar sólo el estado necesario
→ Memory Bootstrap Gate
```

Si el resultado es:

```text
PASS
→ continuar sin crear Wiki por ceremonia
```

Si el resultado es:

```text
BOOTSTRAP REQUIRED
→ crear/conectar sólo checkpoint durable mínimo
→ volver a la unidad original
```

### Evidencia revisada

- `docs/getting-started/adopt-existing-project-from-conversation.md`;
- `docs/foundations/memory-bootstrap-gate.md`;
- `docs/getting-started/bootstrap-llm-wiki.md`;
- `docs/getting-started/incorporate-existing-project-workspace.md`.

### Resultado

`PASS`.

La ausencia de Wiki no bloquea por sí sola. Tampoco se exige reconstruir toda la historia ni reorganizar el proyecto existente.

## Escenario D — Producto nuevo desde cero

### Entrada simulada

- sólo existe una idea inicial;
- no hay app, Wiki, repositorio ni entorno técnico obligatorio todavía.

### Recorrido esperado

```text
00 — Dirección y orquestación / definición inicial
→ propósito + usuario + problema + promesa + prioridad suficientes
→ siguiente resultado verificable
```

Después:

- si puede ejecutarse de forma segura y autosuficiente → Execution Task;
- si falta inspección o diseño técnico → Planning Task;
- si todavía no existe razón para materializar recursos locales → no crear app/wiki/exchange por ceremonia.

### Evidencia revisada

- `docs/getting-started/new-project-from-conversation.md`;
- `docs/getting-started/create-new-project-workspace.md`;
- `docs/foundations/memory-bootstrap-gate.md`.

### Resultado

`PASS`.

IA-DOS permite comenzar desde conversación y materializar sólo los recursos que la siguiente unidad realmente necesite.

## Escenario E — Reanudar proyecto con Wiki existente

### Entrada simulada

- proyecto en curso;
- memoria durable existente;
- conversación nueva o reanudada;
- siguiente unidad depende de parte del estado previo.

### Recorrido esperado

```text
memoria durable vigente
+ implementación/fuentes autorizadas
+ delta de la nueva tarea
→ contexto selectivo
→ Planning Task o Execution Task
```

El coding agent no debe leer toda la Wiki por defecto.

La tarea distingue:

```text
Contexto durable necesario
Referencias Wiki
Lectura requerida
```

### Evidencia revisada

- `docs/foundations/memory-bootstrap-gate.md`;
- `docs/getting-started/bootstrap-llm-wiki.md`;
- `docs/foundations/durable-memory-and-obsidian.md`;
- `docs/orchestration/context-compression-by-authority.md`.

### Resultado

`PASS`.

Una conversación nueva puede rehidratarse desde memoria vigente y la tarea actual sin releer conversaciones anteriores completas.

## Escenario F — Segunda Execution Task en la misma Execution Cell

### Entrada simulada

- existe una Execution Cell activa, por ejemplo `App`;
- la primera Execution Task ya terminó y fue revisada;
- se prepara una segunda unidad distinta dentro de la misma línea de ejecución.

### Recorrido esperado

```text
App · conversación activa
→ Task A
→ Report A
→ revisión
→ Task B
→ misma App
```

La segunda tarea:

- conserva la Execution Cell mientras siga respondiendo bien;
- tiene un Task ID propio;
- vuelve a declarar objetivo, alcance, permisos, criterios y condiciones de detención;
- no hereda autorización de Task A;
- no abre `App · 02` sólo porque cambió la tarea.

Una nueva instancia de la célula sólo aparece ante degradación, contaminación de contexto o necesidad deliberada de contexto limpio.

### Evidencia revisada

- `docs/execution/execution-cells-and-exchange.md`;
- `templates/execution-task-compact.template.md`;
- `templates/execution-task.template.md`;
- `templates/execution-report.template.md`;
- `prompts/getting-started/initialize-project-orchestrator.md`.

### Resultado inicial

`FAIL`.

La plantilla compacta todavía utilizaba:

```text
Agent Session: [RESULTADO]
```

Ese placeholder inducía una identidad de sesión por tarea y contradecía la política de Execution Cells.

### Corrección aplicada

La plantilla compacta ahora utiliza:

```text
Execution Cell o sesión: [NOMBRE O NO APLICA]
```

y declara explícitamente que una Execution Cell activa se reutiliza mientras siga respondiendo bien, sin heredar permisos.

La plantilla completa también fue alineada para priorizar `Execution Cell` y eliminar una referencia residual a `Exchange Protocol v0`.

### Resultado final

`PASS`.

## Defectos encontrados durante la validación

### 1. Nombre antiguo de Exchange en recorridos conversacionales

Se encontraron referencias a `Exchange Protocol v0` en los recorridos de proyecto nuevo y proyecto existente.

Se corrigieron para expresar el modelo vigente:

```text
Exchange
= pasarela pasiva opcional de archivos .md
```

No define contenido, identidad, estados o permisos.

### 2. Sesión de ejecución inferida desde el resultado

La Execution Task compacta todavía podía inducir una conversación por tarea mediante `Agent Session: [RESULTADO]`.

Se corrigió para distinguir una Execution Cell reusable de una sesión independiente cuando el proyecto no adopta células.

### 3. Referencia residual de Exchange en la Execution Task completa

La plantilla completa todavía describía `Exchange Protocol v0` como fuente posible de identificación.

Se corrigió: la identidad pertenece al artefacto construido por el Conversation Agent; Exchange sólo transporta o almacena el `.md`.

## Política deliberadamente abierta

La persistencia o renovación de conversaciones de `Coding Agent — Planning` continúa abierta.

Esta validación confirma únicamente que:

- Planning y Execution permanecen separados;
- no debe inferirse una política de Planning desde Execution Cells;
- ningún recorrido necesita resolver esa política para funcionar correctamente hoy.

Por lo tanto, no constituye un bloqueo para el onboarding consolidado.

## Resultado global

```text
A — nuevo + repo accesible ........ PASS
B — nuevo + offline ............... PASS
C — existente sin Wiki ............ PASS
D — nuevo desde cero .............. PASS
E — reanudar con Wiki ............. PASS
F — segunda Task / misma Cell ..... PASS tras corrección
```

## Conclusión

Los seis recorridos convergen al mismo modelo operativo después de las correcciones detectadas durante esta fase.

No se identificó necesidad de introducir nuevos Conversation Spaces, tipos de artefacto, estados, repositorios, gates, IDs, automatizaciones o roles.

La consolidación puede considerarse coherente para esta fase alpha mientras las futuras modificaciones mantengan equivalencia entre:

- documentación canónica;
- templates operativos;
- onboarding;
- Current Offline Pack.

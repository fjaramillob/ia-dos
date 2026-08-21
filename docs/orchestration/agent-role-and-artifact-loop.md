# Roles, sesiones y ciclo de artefactos

Este contrato define el intercambio repetible entre Conversation Spaces y coding agents.

## Flujo canónico

```text
Persona responsable
→ define dirección y autoridad

Conversation Space / Cycle Owner
→ gobierna resultado dentro de autoridad delegada
→ aplica gates de memoria/readiness cuando corresponda
→ prepara Planning Task | Environment Preflight | Execution Task | Execution Resume

Coding Agent
→ planifica, comprueba readiness o ejecuta según rol y artefacto recibido
→ devuelve artefacto verificable

Cycle Owner
→ revisa

Persona responsable
→ aprueba cuando la decisión excede autoridad delegada
```

Cuando el proyecto utiliza Execution Cells, la ejecución puede ocurrir dentro de una conversación persistente asociada a la célula.

## Roles protegidos

### Persona responsable

Conserva dirección y aprobación final cuando cambian propósito, prioridad, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

### Cycle Owner — Conversation Space

Puede definir el resultado, preparar o validar artefactos, revisar retornos y decidir dentro de la autoridad delegada.

No sustituye la responsabilidad humana ni ejecuta una tarea destinada al coding agent.

### Coding Agent — Planning

Es un rol de solo lectura que admite dos contratos diferentes:

```text
Planning Task
→ Implementation Plan

Environment Preflight
→ Environment Readiness Report
```

Con una `Planning Task` puede inspeccionar, verificar, comparar, proponer y preparar una Execution Task candidata.

Con un `Environment Preflight` sólo comprueba las precondiciones declaradas. No diseña una solución, no modifica el entorno y devuelve readiness.

No puede escribir, aprobar su propio plan o readiness, ejecutar cambios, cambiar Cycle Owner, actuar como `00` ni iniciar otro ciclo.

### Coding Agent — Execution

Admite:

```text
Execution Task
→ Execution Report

Execution Resume
→ Execution Report
```

Puede modificar únicamente lo autorizado, ejecutar verificaciones y producir evidencia.

No puede ampliar alcance, iniciar otra unidad, aprobar su propio resultado, integrar o desplegar sin autorización explícita ni seleccionar la decisión de gobierno posterior.

## Contrato de rol

Una tarea dirigida a un coding agent declara, según corresponda:

```text
Método: IA-DOS
Rol activo: Coding Agent — Planning | Coding Agent — Execution
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [TASK-ID]
Sesión de planificación: [PLAN — RESULTADO | NO APLICA]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Artefacto de entrada: Planning Task | Environment Preflight | Execution Task | Execution Resume
Artefacto de salida: Implementation Plan | Environment Readiness Report | Execution Report
Destino: [CONVERSATION SPACE]
Autoridad: [SOLO LECTURA | ESCRITURA ACOTADA]
```

Compatibilidad canónica:

```text
Coding Agent — Planning + Planning Task
→ Implementation Plan

Coding Agent — Planning + Environment Preflight
→ Environment Readiness Report

Coding Agent — Execution + Execution Task
→ Execution Report

Coding Agent — Execution + Execution Resume
→ Execution Report
```

Usa sólo el campo de sesión/célula pertinente al rol.

## Sesiones de planificación

Planning conserva una frontera explícita de autorización y es siempre de solo lectura.

Puede utilizar un identificador lógico como:

```text
PLAN — [RESULTADO]
```

IA-DOS no establece una política universal sobre persistencia o renovación de conversaciones de Planning. No abras una conversación nueva por tarea sólo por este nombre.

El rol `Coding Agent — Planning` también ejecuta Environment Preflight en solo lectura, pero un preflight no necesita ni implica una sesión `PLAN — ...`.

La planificación nunca se convierte automáticamente en ejecución.

## Environment Preflight

El preflight comparte el rol de solo lectura con Planning, no su propósito.

Debe limitarse a:

- runtime, herramienta, servicio, acceso, secreto o conectividad indispensable declarados;
- comprobaciones no destructivas autorizadas;
- evidencia suficiente para clasificar readiness.

Devuelve:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

No modifica, instala, actualiza, inicia, detiene o configura. `LISTO PARA EJECUCIÓN` permite que el Cycle Owner considere una autorización posterior; no constituye autorización de escritura por sí mismo.

## Execution Cells

Las tareas de ejecución no requieren una conversación nueva por resultado.

Una `Execution Cell` es un contexto durable de ejecución definido por proyecto. Cuando la herramienta ofrece conversaciones persistentes, mantén una conversación activa por célula mientras siga respondiendo bien.

No crees células por especialidad profesional. Crea una nueva sólo cuando separar ese contexto tenga valor operacional real.

La conversación puede renovarse por degradación, contaminación o necesidad real de contexto limpio:

```text
App · 01 → cerrada
App · 02 → activa
```

La célula sigue siendo `App`.

## Autorización no acumulativa

Reutilizar una conversación no reutiliza permisos anteriores.

Cada Execution Task vuelve a declarar:

- objetivo;
- alcance y fuera de alcance;
- autoridad y acceso;
- capacidades autorizadas;
- acciones externas;
- criterios;
- verificaciones;
- condiciones de detención.

## Planning y Execution: separación correcta

La frontera obligatoria es de **rol y autoridad**, no de conversación física.

```text
Planning Task
→ solo lectura
→ Implementation Plan
→ revisión
→ Execution Task autorizada
→ Execution Cell existente o sesión válida
→ Execution Report
```

Una futura Execution Task puede reutilizar una Execution Cell activa aunque el Planning haya ocurrido en otro contexto. Nunca hereda sus permisos.

## Transporte

```text
Execution Task
→ define unidad y límites

Exchange
→ sólo almacena o transporta el .md cuando se utiliza
```

Exchange no cambia el artefacto, no define IDs y no sustituye Execution Cell.

## Identificadores

El Conversation Agent que construye la Execution Task asigna Task ID.

Cuando no existe otro esquema, IA-DOS recomienda:

```text
{PROJECT}-{ORIGIN}-{CELL}-{YYYYMMDD}-{HHMMSS}
```

El Execution Report reutiliza exactamente ese Task ID. `Cycle ID` puede ser `NO APLICA`.

## Acceso a IA-DOS

Una tarea puede usar:

- `Embedded Contract`;
- `Remote Repository`;
- `Local Reference`.

No clones IA-DOS dentro del producto ni crees una referencia local sin autorización.

## Contratos de retorno

### Implementation Plan

```text
Artifact Type: Implementation Plan
Cycle ID: [CYCLE-ID O NO APLICA]
Planning Task ID: [PLAN-ID]
Sesión de planificación: [PLAN — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
```

El plan propone. El coding agent no selecciona por sí mismo aprobación, corrección, rechazo o escalamiento.

### Environment Readiness Report

```text
Artifact Type: Environment Readiness Report
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [PREFLIGHT-ID]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
Cambios realizados: Ninguno
```

El reporte sólo demuestra readiness observado bajo el preflight autorizado.

### Execution Report

```text
Artifact Type: Execution Report
Execution Task ID: [TASK-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

`Atención requerida` identifica un asunto concreto sin elegir la acción de gobierno posterior.

El reporte no incluye por defecto una sección de conocimiento potencialmente durable ni actualización recomendada.

## Gate de revisión

Al recibir un Implementation Plan, el Cycle Owner revisa evidencia, tamaño, seguridad y decisiones pendientes. Obtiene aprobación humana cuando corresponda antes de autorizar una Execution Task.

Al recibir un Environment Readiness Report, confirma que corresponde al preflight vigente. Sólo `LISTO PARA EJECUCIÓN` puede habilitar una autorización posterior de escritura.

Al recibir un Execution Report, compara objetivo, alcance, criterios, autorizaciones y evidencia. Luego decide dentro de la autoridad delegada; la persona responsable interviene cuando corresponde.

La evaluación de memoria ocurre después de revisar evidencia, salvo que la propia tarea haya autorizado una actualización documental concreta.

## Regla principal

```text
Conversation Space = gobierno
Execution Cell = continuidad
Coding Agent — Planning = solo lectura para Planning y Preflight
Execution Task = autoridad de una unidad
Execution Report = evidencia
Persona responsable = aprobación final aplicable
Exchange = transporte pasivo
```

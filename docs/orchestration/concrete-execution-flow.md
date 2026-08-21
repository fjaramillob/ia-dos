# Avance concreto y transición a coding agents

IA-DOS debe producir avances verificables sin depender de una plataforma, proveedor, editor o agente específico.

## Flujo principal

```text
dirección suficiente
→ siguiente resultado verificable
→ asignar Cycle Owner
→ Memory Bootstrap Gate cuando dependa de historia conversacional
→ Environment Preflight cuando readiness indispensable sea desconocido
→ Planning Task cuando falta inspección o diseño
→ Execution Task cuando la unidad está lista
→ artefacto vuelve al Cycle Owner
→ revisión y decisión dentro de la autoridad aplicable
→ persona responsable aprueba cuando corresponde
→ escalar a 00 sólo ante reorientación real
```

`00 — Dirección y orquestación` no es una parada obligatoria entre definición, planificación y ejecución.

## Gate de avance

Evalúa en este orden:

```text
1. ¿El resultado está suficientemente definido, es pequeño y verificable?
2. Si depende de historia, ¿el conocimiento necesario ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿el coding agent puede proponer una primera unidad segura?
```

- memoria necesaria sólo en conversaciones → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección o diseño → `Planning Task`;
- todo listo → `Execution Task`;
- decisión humana indispensable → resolver sólo esa decisión;
- reorientación → escalar a `00`.

## Memory Bootstrap operativo

Cuando el gate devuelve `BOOTSTRAP REQUIRED`:

```text
unidad original
→ queda bloqueada

Execution Task de bootstrap
→ único resultado: checkpoint durable mínimo
→ unidad original fuera de alcance
→ Execution Report
→ revisión
→ reevaluar gate original
```

La tarea de bootstrap no finge `PASS` ni ejecuta el resultado original. Una unidad ordinaria dependiente de esa memoria sólo continúa después de reevaluar el gate y obtener `PASS`.

## Planning Task

La Planning Task solicita al coding agent inspeccionar fuentes y estado real en solo lectura para proponer cómo implementar.

```text
Planning Task
→ Coding Agent — Planning
→ Implementation Plan
→ revisión del Cycle Owner
→ aprobación humana cuando corresponda
→ Execution Task autorizada
```

No autoriza escritura, commits, cambios remotos, despliegues, recursos externos ni costes.

## Gate de tamaño

Antes de aprobar una Execution Task pregunta:

```text
¿Puede completarse, verificarse y reportarse como una sola unidad
sin mezclar resultados independientes ni tomar decisiones mayores nuevas?
```

Si no, divide y autoriza sólo la primera unidad segura.

## Propiedad y responsabilidad

Todo handoff técnico declara Cycle Owner y destino del artefacto de retorno.

El Cycle Owner gobierna dentro de la autoridad delegada. La persona responsable conserva la aprobación final cuando el cambio afecta dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

Planes y reportes no vuelven automáticamente a `00`.

## Readiness del entorno

Cuando una precondición indispensable no está comprobada, usa:

```text
Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

en vez de inferir que el entorno está listo.

Sólo:

```text
LISTO PARA EJECUCIÓN
```

permite considerar aprobación o reanudación de escritura. El readiness report no concede escritura por sí mismo.

No impongas carpeta, repositorio, proveedor, Wiki, plataforma o herramienta específica.

## Transición visible

Cuando corresponda planificación, entrega una `Planning Task` autosuficiente al coding agent en modo de solo lectura y pide devolver el `Implementation Plan` al Cycle Owner.

Cuando corresponda preflight, entrega un `Environment Preflight` al mismo rol de solo lectura y pide devolver `Environment Readiness Report`; no lo conviertas en Planning.

Cuando corresponda ejecución, entrega una `Execution Task` completa a la Execution Cell adecuada o al entorno disponible. Reutiliza una célula activa cuando siga respondiendo bien; no abras una conversación por tarea.

## Revisión del Implementation Plan

El Cycle Owner debe:

1. comprobar fuentes y evidencia;
2. separar hechos, inferencias y propuestas;
3. revisar dependencias, riesgos y condiciones de detención;
4. aplicar el gate de tamaño;
5. identificar decisiones humanas pendientes;
6. autorizar, o solicitar autorización para, una sola primera unidad ejecutable.

Plan producido no equivale a plan aprobado ni a ejecución autorizada.

## Revisión del Execution Report

El destino declarado revisa:

1. objetivo versus resultado;
2. alcance versus cambios reales;
3. criterios versus evidencia;
4. verificaciones solicitadas versus ejecutadas;
5. autorizaciones versus acciones realizadas;
6. fuera de alcance preservado;
7. bloqueos, desviaciones y pendientes del alcance original.

El reporte no selecciona la siguiente acción de gobierno ni propone por defecto qué memoria consolidar.

Después de revisar la evidencia, el Cycle Owner y la persona responsable, según la autoridad aplicable, deciden cierre, corrección, reversión, transferencia, escalamiento o siguiente unidad. Separadamente evalúan si hechos nuevos merecen memoria durable.

Si el reporte corresponde a un memory bootstrap, primero se reevalúa el gate de la unidad original; no se autoriza automáticamente.

## Memoria en la misma ejecución

Una actualización concreta de LLM Wiki puede formar parte de una Execution Task sólo cuando el conocimiento ya está confirmado, la modificación documental está explícitamente autorizada y no requiere una nueva decisión conceptual.

No conviertas toda ejecución de producto en una actualización automática de memoria.

## Guardrails

- no enviar una intención vaga al coding agent;
- no ejecutar antes de resolver decisiones indispensables;
- no omitir Memory Bootstrap Gate cuando existe dependencia chat-only;
- no confundir `BOOTSTRAP REQUIRED` con prohibición de la unidad mínima de checkpoint;
- no omitir Environment Preflight cuando readiness indispensable es desconocido;
- no usar planificación para autorizar escritura implícita;
- no abrir una conversación por cada tarea cuando existe una Execution Cell válida;
- no regresar a `00` por rutina;
- no asumir acceso, permisos o herramientas;
- no declarar completado algo sin evidencia;
- no mezclar objetivos independientes en una sola tarea.

## Regla principal

```text
Conversar sólo lo indispensable.
Persistir memoria sólo cuando haga falta.
Comprobar readiness antes de escribir.
Planificar cuando reduzca incertidumbre real.
Ejecutar unidades pequeñas.
Devolver evidencia al responsable declarado.
Escalar únicamente para reorientar.
```

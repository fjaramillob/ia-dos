# Avance concreto y transición a coding agents

IA-DOS debe producir avances verificables sin depender de una plataforma, proveedor, editor o agente específico.

## Flujo principal

```text
capturar alma y prioridad
→ identificar el siguiente resultado concreto
→ resolver solo la definición indispensable
→ asignar Cycle Owner
→ decidir entre Planning Task y Execution Task
→ devolver el artefacto al destino declarado
→ revisar, corregir o continuar
→ escalar a 00 solo cuando corresponda
```

`00 — Dirección y orquestación` no es una parada obligatoria entre definición, planificación y ejecución.

## Gate de planificación

Cada Cycle Owner debe evaluar:

```text
¿El siguiente resultado está suficientemente definido,
es pequeño y puede ejecutarse con seguridad sin planificación técnica previa?
```

### Sí

Prepara una Execution Task pequeña y verificable.

### No porque falta inspección o diseño técnico

Prepara una Planning Task de solo lectura.

### No porque falta una decisión del mismo dominio

Continúa únicamente hasta resolver esa decisión.

### No porque apareció una cuestión fuera del dominio

Deriva al Conversation Space correspondiente o escala a `00` cuando sea transversal o estratégica.

## Planning Task

La Planning Task solicita al coding agent inspeccionar fuentes y estado real para proponer cómo implementar.

```text
Planning Task
→ inspección en solo lectura
→ Implementation Plan
→ revisión del Cycle Owner
→ aprobación de una unidad
→ Execution Task
```

No autoriza escritura, commits, cambios remotos, despliegues, recursos externos ni costes.

Usa:

- `templates/planning-task.template.md`;
- `templates/implementation-plan.template.md`.

## Gate de tamaño

Antes de aprobar una Execution Task, pregunta:

```text
¿Puede completarse, verificarse y reportarse como una sola unidad
sin mezclar resultados independientes?
```

Si no, divide el plan. No agrupes una iniciativa amplia bajo un solo tipo de ejecución.

## Propiedad y destinos

Todo handoff técnico declara por separado:

- Cycle Owner;
- destino del Implementation Plan;
- destino del Execution Report;
- espacio de escalamiento.

El plan y el reporte no tienen que volver a `00`. Vuelven al espacio responsable indicado.

## Readiness del entorno

Antes de delegar, confirma únicamente:

- entorno disponible: local, remoto o combinado;
- fuentes y artefactos accesibles;
- recursos faltantes;
- trabajo previo que debe preservarse;
- permisos reales;
- datos, secretos o recursos externos restringidos.

No impongas una carpeta, repositorio, proveedor, Wiki, plataforma o herramienta específica.

Consulta `docs/execution/source-and-artifact-authority.md`.

## Transición visible a planificación

Usa una instrucción equivalente a:

> Abre el entorno disponible para el proyecto e inicia una sesión de planificación en solo lectura. Pega la Planning Task siguiente. Devuelve el `Implementation Plan` completo al Conversation Space indicado; no ejecutes cambios.

## Transición visible a ejecución

Usa una instrucción equivalente a:

> Abre el entorno disponible para el proyecto e inicia una sesión de ejecución. Pega la Execution Task siguiente. No amplíes el alcance. Devuelve el `Execution Report` completo al Conversation Space indicado.

El usuario no debe reconstruir la tarea combinando varios mensajes.

## Contenido mínimo de una Planning Task

```text
Cycle Owner y destinos
Objetivo del plan
Contexto mínimo
Autoridad de fuentes, artefactos y entorno
Inspección requerida
Fuera de alcance
Gate de tamaño
Condiciones de detención
Formato del Implementation Plan
```

## Contenido mínimo de una Execution Task

```text
Cycle Owner y destino del reporte
Tipo de ejecución
Objetivo único
Contexto mínimo
Autoridad y acceso de recursos
Alcance y fuera de alcance
Criterios de aceptación
Pruebas o verificaciones
Condiciones de detención
Autorizaciones
Formato del Execution Report
```

## Revisión del Implementation Plan

El Cycle Owner debe:

1. comprobar que el plan se basa en fuentes autorizadas;
2. separar hechos, inferencias y propuestas;
3. revisar contradicciones y riesgos;
4. comprobar dependencias y condiciones de detención;
5. aplicar el gate de tamaño;
6. resolver decisiones humanas pendientes;
7. aprobar solo la primera unidad ejecutable.

Plan producido no equivale a plan aprobado ni a ejecución autorizada.

## Revisión del Execution Report

El destino declarado revisa:

1. objetivo versus resultado;
2. alcance versus cambios reales;
3. criterios versus evidencia;
4. verificaciones solicitadas versus ejecutadas;
5. autorizaciones versus acciones realizadas;
6. estado de memoria y documentación;
7. bloqueos o trabajo parcial;
8. siguiente resultado lógico.

Solo escala a `00` si aparece una condición real de reorientación.

## Producto y memoria en la misma ejecución

La actualización normal de memoria puede incluirse en la Execution Task cuando el conocimiento sea claro, acotado y consecuencia directa del cambio.

No registres propuestas como estado implementado.

## Neutralidad de referencias

Toda tarea y reporte usa únicamente:

- el proyecto actual;
- sus fuentes autorizadas;
- sus recursos reales;
- las capacidades del entorno disponible.

No incluyas detalles de proyectos usados como pruebas salvo que sean fuentes explícitas del proyecto actual.

## Guardrails

- no enviar una intención vaga al coding agent;
- no ejecutar antes de resolver decisiones indispensables;
- no usar planificación para autorizar escritura implícita;
- no abrir otra conversación para posponer una tarea que ya está lista;
- no regresar a `00` por rutina;
- no asumir acceso, permisos o herramientas;
- no declarar completado algo sin evidencia;
- no mezclar objetivos independientes en una sola tarea.

## Regla principal

```text
Conversar solo lo indispensable.
Planificar cuando reduzca incertidumbre real.
Ejecutar unidades pequeñas.
Devolver cada artefacto al responsable declarado.
Escalar únicamente para reorientar.
```
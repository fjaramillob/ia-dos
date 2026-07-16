# Registro de tipos de ejecución

Este registro clasifica cómo debe materializar trabajo un coding agent. No define herramientas concretas ni conversaciones permanentes.

Toda `Execution Task` debe declarar un tipo principal. Puede incluir un tipo secundario solo cuando sea inseparable del mismo resultado.

## Planificación versus ejecución

La planificación técnica no es un tipo de materialización.

```text
Planning Task
→ inspección en solo lectura
→ Implementation Plan
→ revisión del Cycle Owner

Execution Task
→ tipo de ejecución
→ resultado verificable
→ Execution Report
→ revisión del destino declarado
```

Usa una Planning Task cuando todavía sea necesario inspeccionar o diseñar cómo implementar.

Usa una Execution Task solo cuando exista una unidad aprobada, pequeña y verificable.

## Regla general

```text
1 Execution Task
→ 1 tipo principal
→ 1 resultado verificable
→ 1 Execution Report
```

El tipo no concede permisos. Escritura, control de versiones, cambios remotos, despliegue, datos, recursos externos, costes y producción requieren autorización explícita.

## Tipos base

### `INSPECT`

Inspección, auditoría o levantamiento cuyo resultado principal es conocimiento o evidencia, no un plan de implementación.

- modo predeterminado: solo lectura;
- evidencia: fuentes, hallazgos y límites;
- detenerse si la verificación exige acciones no autorizadas.

Una inspección puede informar una Planning Task posterior, pero no la sustituye cuando aún falta diseñar la secuencia de implementación.

### `BOOTSTRAP`

Inicialización mínima de una estructura, producto, memoria o configuración base.

- exige estructura objetivo y archivos mínimos confirmados;
- no debe elegir arquitectura no aprobada;
- evidencia: estado creado y verificaciones básicas.

### `BUILD`

Construcción de una capacidad nueva o incremento funcional.

- exige comportamiento esperado y criterios observables;
- debe preservar lo que queda fuera de alcance;
- evidencia: cambios, pruebas y revisión funcional.

### `FIX`

Corrección de un defecto reproducible.

- exige síntoma, evidencia inicial y resultado esperado;
- no autoriza refactors amplios;
- evidencia: reproducción previa, corrección y regresión cuando aplique.

### `REFACTOR`

Cambio interno que debe preservar comportamiento externo.

- exige invariantes explícitas;
- no introduce capacidades nuevas por omisión;
- evidencia: pruebas y comparación del comportamiento relevante.

### `MIGRATE`

Traslado selectivo de código, datos, estructura, proveedor o arquitectura.

- exige fuente, destino, estrategia y reversibilidad cuando aplique;
- no autoriza copiar todo automáticamente;
- evidencia: mapeo, compatibilidad y riesgos remanentes.

### `TEST`

Creación, reparación o fortalecimiento de verificaciones.

- exige qué riesgo o comportamiento debe comprobarse;
- no debe alterar comportamiento solo para hacer pasar una prueba sin autorización;
- evidencia: pruebas agregadas y resultado.

### `HARDEN`

Mejora de seguridad, aislamiento, rendimiento, resiliencia o cumplimiento técnico.

- exige amenaza, riesgo o límite medible;
- puede requerir planificación previa;
- evidencia: riesgo mitigado, pruebas y efectos colaterales.

### `DOCUMENT`

Creación o actualización de documentación técnica, pública u operativa.

- exige audiencia, propósito y fuentes autorizadas;
- no presenta propuestas como implementación;
- evidencia: artefactos, navegación y coherencia.

### `WIKI`

Actualización de memoria durable del proyecto.

- distingue hechos, decisiones, hipótesis y desconocidos;
- no copia chats o reportes completos sin síntesis;
- evidencia: páginas actualizadas y fuentes.

### `RELEASE`

Preparación o ejecución autorizada de una entrega.

- exige versión, artefacto, entorno, verificaciones y reversión cuando corresponda;
- producción e integración final no se presumen autorizadas;
- evidencia: checks y estado de entrega.

### `OPERATE`

Trabajo sobre infraestructura, observabilidad, continuidad o mantenimiento operativo.

- exige entorno, impacto, ventana y límites de acceso;
- minimiza cambios irreversibles;
- evidencia: estado anterior y posterior, comandos, métricas o registros.

## Selección rápida

| Resultado dominante | Artefacto o tipo |
|---|---|
| Diseñar cómo implementar sin escribir | `Planning Task` |
| Comprender o auditar sin cambiar | `INSPECT` |
| Crear la base mínima | `BOOTSTRAP` |
| Añadir capacidad | `BUILD` |
| Corregir un defecto | `FIX` |
| Mejorar estructura preservando comportamiento | `REFACTOR` |
| Trasladar o converger | `MIGRATE` |
| Aumentar verificación | `TEST` |
| Reducir riesgo técnico | `HARDEN` |
| Documentar | `DOCUMENT` |
| Mantener memoria durable | `WIKI` |
| Entregar una versión | `RELEASE` |
| Operar un entorno | `OPERATE` |

## Gate de tamaño

Antes de aprobar una Execution Task, verifica:

```text
¿Tiene un solo resultado terminable y no mezcla fases independientes?
```

Si el trabajo contiene varias unidades, usa o revisa un Implementation Plan y aprueba solo la primera.

Un tipo principal compartido no convierte varios resultados en una sola tarea.

## Campos que hereda la tarea

El tipo elegido influye en:

- modo de acceso y escritura;
- evidencia inicial requerida;
- criterios de aceptación;
- pruebas mínimas;
- autorizaciones;
- condiciones de detención;
- formato del Execution Report;
- necesidad de actualizar documentación o memoria.

La `Execution Task` sigue siendo la autoridad concreta. Este registro aporta valores predeterminados y evita que cada coding agent improvise el modo de trabajo.
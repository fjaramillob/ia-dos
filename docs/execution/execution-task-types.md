# Registro de tipos de ejecución

Este registro clasifica cómo debe materializar trabajo un coding agent. No define herramientas concretas ni conversaciones permanentes.

Toda `Execution Task` debe declarar un tipo principal. Puede incluir un tipo secundario sólo cuando sea inseparable del mismo outcome.

## Planificación versus ejecución

La planificación técnica no es un tipo de materialización.

```text
Planning Task
→ inspección en solo lectura
→ Implementation Plan
→ revisión del Cycle Owner

Execution Task
→ tipo de ejecución
→ outcome verificable
→ Execution Report
→ revisión del destino declarado
```

Usa una Planning Task cuando todavía sea necesario inspeccionar o diseñar cómo implementar.

Usa una Execution Task cuando exista un resultado definido, cohesivo, acotado y verificable bajo una frontera estable de autoridad.

## Regla general

```text
1 Execution Task
→ 1 outcome cohesivo
→ 1 frontera estable de autoridad
→ 1 Execution Report
```

El tipo no concede permisos. Escritura, control de versiones, cambios remotos, despliegue, datos, recursos externos, costes y producción requieren autorización explícita dentro de la Execution Task.

Una Task no debe dividirse sólo por duración, cantidad de archivos o comandos, ni porque contenga fases internas de implementación, tests, commit, push, deploy o smoke. IA-DOS busca maximizar el resultado seguro y verificable por Task, no la cantidad de Tasks.

## Tipos base

### `INSPECT`

Inspección, auditoría o levantamiento cuyo resultado principal es conocimiento o evidencia, no un plan de implementación.

- modo predeterminado: solo lectura;
- evidencia: fuentes, hallazgos y límites;
- detenerse si la verificación exige acciones no autorizadas.

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
- no autoriza refactors amplios por defecto;
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
- no debe alterar comportamiento sólo para hacer pasar una prueba sin autorización;
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

Actualización autorizada de memoria durable del proyecto.

- exige que la propia Execution Task delimite el conocimiento y las rutas que puede modificar;
- distingue hechos, decisiones, hipótesis y desconocidos;
- no copia chats o reportes completos sin síntesis;
- evidencia: páginas actualizadas y fuentes.

### `RELEASE`

Preparación o ejecución autorizada de una entrega.

- exige versión, artefacto, entorno, verificaciones y reversión cuando corresponda;
- integración, despliegue y producción no se presumen autorizados, pero pueden formar parte del mismo Authority Envelope cuando sirven al mismo outcome;
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
| Mantener memoria durable con autorización explícita | `WIKI` |
| Entregar una versión | `RELEASE` |
| Operar un entorno | `OPERATE` |

## Gate de granularidad

Antes de aprobar una Execution Task, verifica:

```text
¿El trabajo persigue un outcome cohesivo y verificable
bajo una frontera de autoridad que puede mantenerse estable hasta el Final State?
```

Puede incluir múltiples fases internas si todas son inseparables del mismo resultado.

Divide o detén cuando cambie materialmente:

- outcome;
- scope;
- autoridad;
- arquitectura;
- seguridad;
- datos;
- riesgo;
- coste;
- entorno.

Un tipo principal compartido no convierte outcomes independientes en una sola tarea.

## Authority Envelope

La Task puede agrupar permisos explícitos de Code, Git, Delivery, Production, datos o servicios externos.

```text
acción sensible no declarada
→ no autorizada

acción declarada + gates previos cumplidos + frontera estable
→ puede ejecutarse dentro de la misma Task
```

El Authority Envelope no es un Artifact Type y el coding agent no aprueba su propio plan o ejecución.

## Campos que hereda la tarea

El tipo elegido influye en:

- modo de acceso y escritura;
- evidencia inicial requerida;
- criterios de aceptación;
- pruebas mínimas;
- autorizaciones;
- condiciones de detención;
- formato proporcional del Execution Report;
- documentación o memoria que la propia Execution Task autorice modificar como parte de su outcome.

La `Execution Task` sigue siendo la autoridad concreta. Este registro aporta valores predeterminados y evita que cada coding agent improvise el modo de trabajo.
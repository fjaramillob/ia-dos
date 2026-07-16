# Registro de tipos de ejecución

Este registro clasifica cómo debe trabajar un coding agent. No define herramientas concretas ni conversaciones permanentes.

Toda `Execution Task` debe declarar un tipo principal. Puede incluir un tipo secundario solo cuando sea inseparable del resultado principal.

## Regla general

```text
1 Execution Task
→ 1 tipo principal
→ 1 resultado verificable
→ 1 Execution Report
→ retorno al Conversation Space de origen
```

El tipo no concede permisos. Escritura, commits, push, pull request, merge, despliegue, datos, costes y producción requieren autorización explícita.

## Tipos base

### `INSPECT`

Inspección, auditoría o levantamiento sin modificar artefactos.

- modo predeterminado: solo lectura;
- evidencia: fuentes, rutas, hallazgos y límites de la inspección;
- detenerse si la verificación exige secretos, escritura o acciones externas.

### `BOOTSTRAP`

Inicialización mínima de estructura, repositorio, aplicación, Wiki o configuración base.

- exige estructura objetivo y archivos mínimos;
- no debe elegir arquitectura no confirmada;
- evidencia: árbol creado, estado Git y verificaciones básicas.

### `BUILD`

Construcción de una capacidad nueva o incremento funcional.

- exige comportamiento esperado y criterios observables;
- debe preservar lo que queda fuera de alcance;
- evidencia: diff, pruebas aplicables y revisión funcional.

### `FIX`

Corrección de un defecto reproducible.

- exige síntoma, evidencia inicial y resultado esperado;
- no autoriza refactors amplios;
- evidencia: reproducción previa, corrección y prueba de regresión cuando aplique.

### `REFACTOR`

Cambio interno que debe preservar comportamiento externo.

- exige invariantes explícitas;
- no debe introducir capacidades nuevas por omisión;
- evidencia: pruebas existentes, diff y comparación del comportamiento relevante.

### `MIGRATE`

Traslado selectivo de código, datos, estructura, proveedor o arquitectura.

- exige fuente, destino, estrategia de convergencia y reversibilidad cuando aplique;
- no autoriza copiar todo automáticamente;
- evidencia: matriz o mapeo, compatibilidad y riesgos remanentes.

### `TEST`

Creación, reparación o fortalecimiento de verificaciones.

- exige qué riesgo o comportamiento debe comprobarse;
- no debe alterar comportamiento solo para hacer pasar una prueba sin autorización;
- evidencia: pruebas agregadas, resultado y cobertura del riesgo definido.

### `HARDEN`

Mejora de seguridad, aislamiento, rendimiento, resiliencia o cumplimiento técnico.

- exige amenaza, riesgo o límite medible;
- puede requerir revisión especializada antes de escribir;
- evidencia: riesgo mitigado, pruebas y efectos colaterales evaluados.

### `DOCUMENT`

Creación o actualización de documentación técnica, pública u operativa.

- exige audiencia, propósito y fuentes autorizadas;
- no debe presentar propuestas como implementación;
- evidencia: archivos, navegación, enlaces y coherencia editorial.

### `WIKI`

Actualización de memoria durable del proyecto.

- exige distinguir hechos, decisiones, hipótesis y desconocidos;
- no debe copiar chats o reportes completos sin síntesis;
- evidencia: páginas actualizadas, fuentes y navegación.

### `RELEASE`

Preparación o ejecución autorizada de una entrega.

- exige versión, artefacto, entorno, verificaciones y plan de reversión cuando corresponda;
- producción y merge no se presumen autorizados;
- evidencia: checks, artefactos, estado de entrega y desviaciones.

### `OPERATE`

Trabajo sobre infraestructura, observabilidad, continuidad o mantenimiento operativo.

- exige entorno, impacto, ventana y límites de acceso;
- debe minimizar cambios irreversibles;
- evidencia: estado anterior y posterior, comandos, métricas o registros aplicables.

## Selección rápida

| Resultado dominante | Tipo |
|---|---|
| Comprender sin cambiar | `INSPECT` |
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

## Campos que hereda la tarea

El tipo elegido debe influir en:

- modo de acceso y escritura;
- evidencia inicial requerida;
- criterios de aceptación;
- pruebas mínimas;
- autorizaciones explícitas;
- condiciones de detención;
- formato del `Execution Report`;
- necesidad de actualizar documentación o Wiki.

La `Execution Task` sigue siendo la autoridad concreta. Este registro aporta valores predeterminados y evita que cada coding agent improvise el modo de trabajo.
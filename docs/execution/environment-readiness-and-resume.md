# Readiness del entorno y reanudación

Este contrato evita autorizar escritura antes de comprobar dependencias indispensables y permite reanudar una tarea bloqueada sin replantearla cuando sus fronteras siguen intactas.

## Continuidad

Cuando el proyecto ya está en desarrollo:

- conserva el Cycle Owner y los identificadores aplicables;
- no repite onboarding, clasificación ni decisiones confirmadas;
- no vuelve a `00` salvo reorientación real;
- continúa desde el último artefacto válido o estado bloqueado.

Una conversación de Execution Cell puede reutilizarse mientras siga respondiendo bien. La conversación no hereda permisos de tareas anteriores.

## Readiness antes de ejecutar

Antes de aprobar o iniciar escritura, comprueba sólo las precondiciones indispensables para la tarea:

- runtime y versión;
- herramienta requerida;
- servicio, daemon o contenedor operativo;
- acceso y permisos;
- secretos o conectividad necesarios sin exponer valores;
- recursos externos y costes relevantes;
- estado que debe preservarse.

Estados canónicos:

```text
LISTO PARA EJECUCIÓN | NO LISTO | DESCONOCIDO
```

Sólo `LISTO PARA EJECUCIÓN` permite aprobar o reanudar escritura.

Una herramienta instalada no demuestra que su servicio esté operativo.

## Environment Preflight

Úsalo cuando una dependencia indispensable no esté comprobada.

El preflight:

- es de solo lectura respecto del proyecto y entorno inspeccionados;
- no crea ni modifica archivos del proyecto/entorno;
- puede materializar únicamente su propio `Environment Readiness Report` cuando `Output Delivery` lo autoriza explícitamente;
- no instala o actualiza;
- no inicia, detiene o configura servicios;
- no ejecuta la Execution Task;
- devuelve un `Environment Readiness Report`.

La materialización del reporte autorizado no convierte el preflight en ejecución ni concede permisos de escritura sobre el entorno.

## Acciones sobre el entorno

Distingue siempre:

```text
inspeccionar
≠ usar un servicio ya operativo
≠ iniciar o reiniciar
≠ configurar
≠ instalar o actualizar
```

Cada `Execution Task` declara por separado las capacidades autorizadas.

## Bloqueo válido

Cuando una precondición falla durante ejecución:

1. detén la tarea;
2. devuelve un `Execution Report` con `Estado: BLOQUEADO`;
3. registra evidencia y la atención concreta requerida;
4. conserva la tarea como candidata a reanudación sólo si objetivo, alcance, autoridad, seguridad y arquitectura siguen sin cambios;
5. no replanifiques por defecto.

## Execution Resume

`Execution Resume` reanuda la **misma Execution Task** después de resolver una condición bloqueante.

Sólo es válido cuando permanecen sin cambios:

- objetivo;
- alcance;
- autoridad;
- seguridad;
- arquitectura;
- resultado verificable esperado.

Contrato mínimo:

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: nueva Planning Task | replantear arquitectura | ampliar alcance
Cycle ID: [MISMO CYCLE-ID O NO APLICA]
Task ID: [MISMO TASK-ID]
Execution Cell o sesión: [NOMBRE O NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
```

Incluye únicamente:

- condición que bloqueó;
- evidencia de resolución;
- verificación previa no destructiva;
- punto exacto de reanudación;
- permisos vigentes de la tarea original;
- cambios externos relevantes;
- destino del reporte.

No abre un ciclo nuevo por sí mismo y no amplía permisos.

Si cambió objetivo, alcance, autoridad, seguridad, arquitectura o resultado verificable, no uses Resume: prepara una nueva `Execution Task` o vuelve a Planning cuando corresponda.

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

Toda Execution Task comienza con una fase de `Revalidate` sobre las precondiciones volátiles indispensables para la acción que va a realizar o la Protected Boundary que va a cruzar.

Antes de aprobar una frontera sensible mediante Preflight separado, o antes de cruzarla durante Execution, comprueba sólo las precondiciones indispensables:

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

No es una fase obligatoria previa a toda Execution.

Úsalo cuando:

- el readiness debe conocerse antes de conceder autoridad sensible;
- la disponibilidad/capacidad del entorno es en sí misma el resultado que se quiere evaluar;
- la inspección requiere un actor, credencial o entorno distinto del executor;
- existe incertidumbre material que el Cycle Owner necesita resolver antes de autorizar escritura.

Si la Execution Task ya está autorizada y sólo necesita revalidar estado volátil, usa `Revalidate` dentro de la propia ejecución.

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

## Fallo técnico versus bloqueo válido

Con `Adaptation Authority: BOUNDED`, un fallo técnico ordinario no obliga a cerrar la ejecución como `BLOQUEADO` cuando:

- no produjo side effects materiales o irreversibles;
- outcome, Protected Invariants y Protected Boundaries siguen intactos;
- la corrección usa capacidades ya autorizadas;
- existe una ruta razonable de reparación y verificación.

En ese caso: diagnostica, repara, revalida y continúa dentro de la misma Task.

Devuelve `BLOQUEADO` cuando:

1. la condición no puede resolverse dentro de la autoridad vigente;
2. requiere acción externa, humana o un recurso no disponible;
3. aparece estado parcial/irreversible no cubierto por recovery;
4. cambia outcome, Protected Invariants, scope, autoridad, seguridad, arquitectura o Protected Boundary;
5. no existe evidencia suficiente para un safe retry.

No replanifiques por defecto.

## Execution Resume

`Execution Resume` reanuda la **misma Execution Task** después de resolver una condición bloqueante externa o una interrupción real.

No es necesario para debugging, repair-in-place o safe retry que ocurrieron mientras la misma ejecución seguía abierta bajo `Adaptation Authority: BOUNDED`.

Sólo es válido cuando permanecen sin cambios:

- outcome;
- Protected Invariants;
- alcance;
- autoridad;
- seguridad;
- arquitectura;
- Protected Boundaries;
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

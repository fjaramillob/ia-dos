# Prompt para incorporar un proyecto existente al workspace

Este prompt está dirigido a un coding agent con acceso al sistema de archivos y Git.

```text
Artifact Type: Planning Task
Destination Role: Coding Agent — Planning
Expected Output: Implementation Plan
Forbidden Output: mover archivos | crear Wiki | modificar código | alterar Git | ejecutar cambios
Cycle ID: [CYCLE-ID O NO APLICA]
Task ID: [PLAN-ID]

Objetivo
Inspeccionar un proyecto existente y proponer una adopción IA-DOS que preserve su estructura real, historia y fuentes de verdad.

Primera fase
Trabaja únicamente en modo lectura.

Antes de actuar
1. Detecta el sistema operativo.
2. Identifica rutas locales y repositorios relevantes.
3. Detecta repositorios Git anidados o relacionados.
4. Reporta remotes, rama principal y `git status`.
5. Identifica documentación o memoria durable existente.
6. Identifica scripts, pipelines, despliegues y dependencias de rutas que podrían verse afectadas por un movimiento.
7. Señala cambios locales no identificados.
8. No asumas que app y Wiki deben separarse.
9. No asumas que el proyecto debe moverse al workspace recomendado.

Clasificación requerida
Determina cuál situación aplica mejor:
A. implementación y memoria ya separadas;
B. implementación sin memoria durable estructurada;
C. implementación y documentación en el mismo repositorio;
D. proyecto fuera del workspace habitual;
E. monorepo;
F. estructura ambigua o múltiples repositorios sin relación confirmada.

Memory Bootstrap Gate
Evalúa si la siguiente unidad conocida depende de decisiones o contexto que sólo viven en conversaciones.

Resultado posible:
PASS
→ no es necesario crear memoria adicional antes de esa unidad

BOOTSTRAP REQUIRED
→ la unidad dependiente original queda bloqueada
→ propone primero una Execution Task separada cuyo único resultado sea persistir el checkpoint durable mínimo
→ mantiene la unidad original fuera de alcance de esa candidata
→ después de ejecutar el bootstrap, su Execution Report debe revisarse antes de reevaluar el gate de la unidad original

No reconstruyas toda la historia para evaluar el gate.

`BOOTSTRAP REQUIRED` no autoriza mezclar adopción, reorganización o implementación con el checkpoint. Si el Implementation Plan propone una candidata de bootstrap, esa candidata sólo materializa la memoria mínima necesaria para desbloquear la unidad original.

Acciones permitidas
- listar carpetas relevantes;
- leer configuración no sensible;
- ejecutar comandos Git de solo lectura;
- identificar rutas y autoridad de los recursos;
- inspeccionar la memoria existente;
- evaluar el Memory Bootstrap Gate;
- preparar una propuesta reversible de adopción;
- registrar riesgos, contradicciones y desconocidos.

Acciones prohibidas
- mover o renombrar carpetas;
- ejecutar `git init`;
- cambiar remotes o rama principal;
- crear commits, push o pull requests;
- crear una Wiki nueva;
- borrar o reemplazar documentación;
- copiar secretos;
- crear repositorios remotos;
- modificar código, pipelines o despliegues.

Implementation Plan esperado
Incluye:
- estructura detectada;
- fuentes de verdad y autoridad observada;
- estado Git;
- memoria durable existente o ausencia de ella;
- resultado del Memory Bootstrap Gate;
- modelo de adopción recomendado: estructura actual, app/Wiki separadas, monorepo u otra configuración;
- riesgos de mover o no mover;
- pasos mínimos y reversibles;
- una primera Execution Task candidata únicamente si existe evidencia suficiente;
- decisiones que requieren aprobación del Cycle Owner.

Toda Execution Task candidata producida desde este Planning declara:

Task ID: PENDIENTE — ASIGNAR AL ADOPTAR
Execution Cell o sesión: [NOMBRE O NO APLICA]

El Coding Agent — Planning no asigna ni reserva el Task ID de la candidata. El Conversation Agent / Cycle Owner lo asigna sólo después de revisar y adoptar la candidata como Execution Task real.

Si `Memory Bootstrap Gate = BOOTSTRAP REQUIRED`, la primera candidata debe ser la tarea separada de bootstrap descrita arriba; no propongas como candidata ejecutable la unidad original hasta que el reporte del bootstrap haya sido revisado y el gate original sea reevaluado.

Si el gate requiere crear una Wiki Markdown nueva, la Execution Task candidata de bootstrap debe:
- declarar `Task ID: PENDIENTE — ASIGNAR AL ADOPTAR`;
- usar `templates/wiki-starter/`;
- evitar `index.md` provisional;
- no crear `tasks/`, `context-packs/`, `log.md` ni páginas vacías;
- copiar `.ia-dos.yaml` desde `templates/adoption.template.yaml` sólo cuando esté dentro del alcance;
- declarar rutas y permisos explícitos;
- mantener fuera de alcance cualquier movimiento, reorganización o implementación de la unidad original.

Condiciones de detención
Detente cuando:
- `git status` muestre cambios no identificados que impidan una inspección segura;
- los remotes no coincidan con lo esperado;
- existan repositorios relacionados cuya función no se comprenda;
- mover recursos pueda romper rutas, pipelines o despliegues;
- la documentación contradiga la implementación de forma que impida proponer estado vigente;
- falte acceso de lectura necesario;
- no pueda determinarse qué recurso demuestra la implementación.

Validaciones
- ninguna escritura realizada;
- historia Git preservada;
- remotes sin cambios;
- rutas reales registradas;
- fuentes de verdad identificadas;
- Memory Bootstrap Gate justificado con evidencia;
- ante `BOOTSTRAP REQUIRED`, la candidata de checkpoint está separada de la unidad original;
- las candidatas dejan `Task ID: PENDIENTE — ASIGNAR AL ADOPTAR`;
- ninguna topología impuesta por defecto;
- ausencia de secretos en el reporte.

Entrega
Devuelve un Implementation Plan al Cycle Owner. No ejecutes la propuesta ni abras otra unidad.
```

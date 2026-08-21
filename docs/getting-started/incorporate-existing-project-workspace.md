# Incorporar un proyecto existente al workspace

Esta guía formaliza un proyecto que ya tiene código, documentación, repositorios o despliegues dentro de un workspace IA-DOS.

El objetivo no es moverlo ni renombrarlo automáticamente. Primero se inspecciona su situación real, se define el modelo de adopción y se documentan únicamente las excepciones que afecten la forma de trabajo.

## Antes de comenzar

Debes contar con:

- acceso al proyecto existente;
- una ruta local conocida o un remote confirmado;
- autorización para inspeccionar su estructura;
- un workspace elegido, cuando corresponda;
- IA-DOS disponible por referencia remota o local.

La primera fase debe realizarse en modo lectura.

## Paso 1 — Identificar la realidad actual

Registra:

- nombre del proyecto;
- ruta local, cuando exista;
- remote o remotes Git;
- rama principal;
- estado del working tree;
- repositorios relacionados;
- documentación o memoria existente;
- backlog o mecanismo de seguimiento existente;
- Exchange existente, si lo hay;
- pipelines, despliegues e integraciones relevantes;
- dependencias de rutas que podrían romperse al mover recursos.

No supongas que una carpeta equivale a un solo repositorio ni expongas secretos para describir su ubicación.

## Paso 2 — Clasificar la estructura existente

Identifica cuál situación describe mejor el proyecto.

### Implementación y memoria ya separadas

Verifica que ambas sigan siendo fuentes útiles y que la memoria represente estado vigente.

### Implementación sin memoria durable estructurada

Mantén la implementación donde está. Antes de crear una Wiki hermana evalúa el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md).

### Implementación y documentación en el mismo repositorio

No separes automáticamente. Evalúa sólo si la estructura actual impide mantener o consumir conocimiento con claridad.

### Proyecto fuera del workspace habitual

No lo muevas por estética. Conserva su ubicación y adopta por referencia cuando moverlo agregue riesgo sin beneficio operacional.

### Monorepo

Mantén el monorepo cuando sea una decisión real del proyecto. Documenta la ubicación de implementación y memoria sin forzar repositorios adicionales.

### Estructura ambigua

Si existen varios repositorios, rutas o fuentes y no puede determinarse su relación, detente antes de escribir y devuelve la ambigüedad al Cycle Owner.

## Paso 3 — Elegir el modelo de adopción

IA-DOS acepta, entre otros:

```text
proyecto/
├── proyecto-app/
└── proyecto-wiki/
```

```text
repositorio-monorepo/
├── app/
└── docs/
```

```text
ruta-existente/proyecto-app/
otra-ruta/proyecto-wiki/
```

Exchange puede vivir como recurso hermano, subdirectorio, carpeta sincronizada, repositorio independiente o no existir.

La topología elegida debe preservar historia, accesos y rutas reales. No necesita coincidir con un ejemplo mientras las fuentes de verdad y la forma de acceso sean claras.

## Paso 4 — Incorporar la implementación sin alterar su historia

Cuando el repositorio ya existe:

- no ejecutes `git init` nuevamente;
- no reemplaces remotes;
- no cambies la rama principal;
- no hagas commits automáticos;
- no muevas archivos para normalizar estructura sin una tarea específica;
- no elimines documentación antes de comprender su autoridad.

Si debe clonarse, usa una carpeta vacía y confirma el destino antes de ejecutar `git clone`.

## Paso 5 — Evaluar el Memory Bootstrap Gate

Antes de delegar una unidad que dependa de historia o decisiones previas pregunta:

> ¿La siguiente unidad puede ejecutarse correctamente sin reconstruir conocimiento relevante desde conversaciones?

```text
PASS
→ continúa sin crear memoria adicional por ceremonia

BOOTSTRAP REQUIRED
→ la unidad dependiente original queda bloqueada
→ prepara una Execution Task separada cuyo único resultado sea crear o conectar el checkpoint durable mínimo
→ mantén la unidad original fuera de alcance
→ revisa el Execution Report de esa tarea
→ reevalúa el gate de la unidad original
```

`BOOTSTRAP REQUIRED` no autoriza mezclar el checkpoint con la adopción, reorganización, Planning, Preflight o Execution que lo originó.

No conviertas esta evaluación en una auditoría integral.

## Paso 6 — Crear o conectar la memoria, cuando corresponda

Si el gate devuelve `BOOTSTRAP REQUIRED`, la creación o actualización del checkpoint se materializa mediante la Execution Task separada indicada en el paso anterior. Esa tarea sólo persiste la memoria mínima necesaria para desbloquear la unidad original.

Si ya existe una Wiki o documentación durable:

- conserva sus rutas cuando sean claras;
- identifica su home o punto de entrada;
- registra el estado vigente y las fuentes de verdad;
- no renombres archivos sólo para coincidir con el starter actual.

Si debe crearse una Wiki Markdown nueva, usa `templates/wiki-starter/` y [Crear o conectar la memoria durable](bootstrap-llm-wiki.md).

No crees un `index.md` provisional ni una carpeta de tareas dentro de la Wiki por defecto.

Después de ejecutar el bootstrap, revisa su `Execution Report`. Esa revisión no desbloquea automáticamente la unidad original: primero vuelve a evaluar su Memory Bootstrap Gate.

## Paso 7 — Evaluar Exchange por separado

La necesidad de Exchange no se deriva automáticamente de tener una Wiki, varias conversaciones o muchas tareas.

Úsalo sólo cuando una pasarela de archivos Markdown entre Conversation Agent y Code Agent aporte valor.

Si ya existe un mecanismo equivalente:

- conserva su historia;
- determina si es realmente una pasarela, backlog, memoria u otra cosa;
- no migres ni renombres artefactos por estética;
- no le atribuyas generación de IDs, templates, estados o decisiones si no la tiene.

Si se decide usar Exchange, consulta [Crear o conectar Exchange](bootstrap-exchange.md).

## Paso 8 — Registrar la adopción

Cuando se necesite configuración reproducible, crea `.ia-dos.yaml` desde `templates/adoption.template.yaml` y registra sólo recursos reales:

| Elemento | Registro mínimo |
|---|---|
| Proyecto | nombre y slug cuando exista |
| Implementación | ruta o URL |
| Memoria | ruta, URL o `NO APLICA` |
| Backlog | ruta, URL o `NO APLICA` |
| Exchange | ruta, URL o `NO APLICA` |
| IA-DOS | versión o commit adoptado |
| Project Orchestrator | entorno conversacional utilizado |
| Excepciones | motivo e impacto cuando existan |

Exchange se registra sólo como recurso de transporte; no como fuente de tareas.

## Verificación

Antes de considerar el proyecto incorporado, confirma:

- [ ] La historia Git fue preservada.
- [ ] Los remotes no fueron modificados sin autorización.
- [ ] No se movieron archivos por normalización estética.
- [ ] Las fuentes de verdad relevantes están identificadas.
- [ ] El modelo de adopción refleja la estructura real.
- [ ] El Memory Bootstrap Gate fue evaluado cuando la siguiente unidad depende de contexto histórico.
- [ ] Ante `BOOTSTRAP REQUIRED`, el checkpoint se materializa mediante una Execution Task separada y la unidad original queda fuera de alcance.
- [ ] El Execution Report del bootstrap se revisa antes de reevaluar la unidad original.
- [ ] La memoria existente fue preservada o el starter vigente se utilizó para una Wiki nueva.
- [ ] Exchange, si existe, se mantiene como pasarela pasiva y no como backlog, memoria o generador de identidad.
- [ ] No se asumió automatización inexistente.
- [ ] No se expusieron secretos.
- [ ] Las rutas reales fueron reportadas.

## Condiciones de detención

Detente cuando:

- el working tree tenga cambios no identificados;
- el remote no coincida con lo esperado;
- existan repositorios relacionados cuya función no se comprenda;
- mover recursos pueda romper rutas, pipelines o despliegues;
- la documentación contradiga la implementación de forma relevante;
- falte autorización para clonar, mover, inicializar Git o crear archivos;
- no pueda determinarse qué recurso demuestra la implementación actual.

## Siguiente paso

Si `Memory Bootstrap Gate = BOOTSTRAP REQUIRED`, ejecuta únicamente la tarea separada de checkpoint, revisa su `Execution Report` y reevalúa el gate. Sólo después de obtener `PASS` vuelve a la Planning Task, Environment Preflight o Execution Task original.

Si se decidió utilizar Exchange, crea o conecta únicamente la pasarela mediante una acción separada y autorizada cuando corresponda.

No conviertas la incorporación en un proyecto paralelo ni mezcles en una sola unidad bootstrap de memoria y trabajo original.

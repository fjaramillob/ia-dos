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

- `PASS`: continúa sin crear memoria adicional por ceremonia.
- `BOOTSTRAP REQUIRED`: crea o conecta un checkpoint durable mínimo.

No conviertas esta evaluación en una auditoría integral.

## Paso 6 — Crear o conectar la memoria, cuando corresponda

Si ya existe una Wiki o documentación durable:

- conserva sus rutas cuando sean claras;
- identifica su home o punto de entrada;
- registra el estado vigente y las fuentes de verdad;
- no renombres archivos sólo para coincidir con el starter actual.

Si debe crearse una Wiki Markdown nueva, usa `templates/wiki-starter/` y [Crear o conectar la memoria durable](bootstrap-llm-wiki.md).

No crees un `index.md` provisional ni una carpeta de tareas dentro de la Wiki por defecto.

## Paso 7 — Registrar la adopción

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

## Verificación

Antes de considerar el proyecto incorporado, confirma:

- [ ] La historia Git fue preservada.
- [ ] Los remotes no fueron modificados sin autorización.
- [ ] No se movieron archivos por normalización estética.
- [ ] Las fuentes de verdad relevantes están identificadas.
- [ ] El modelo de adopción refleja la estructura real.
- [ ] El Memory Bootstrap Gate fue evaluado cuando la siguiente unidad depende de contexto histórico.
- [ ] La memoria existente fue preservada o el starter vigente se utilizó para una Wiki nueva.
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

Si el Memory Bootstrap Gate requiere memoria, crea o actualiza sólo el checkpoint mínimo y vuelve a la unidad que originó esa necesidad.

Si el gate pasa, continúa con la siguiente Planning Task, Environment Preflight o Execution Task sin convertir la adopción en un proyecto paralelo.
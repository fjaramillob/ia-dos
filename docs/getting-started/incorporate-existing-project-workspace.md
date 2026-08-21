# Incorporar un proyecto existente al workspace

Esta guía formaliza un proyecto que ya tiene código, documentación, repositorios o despliegues dentro de un workspace IA-DOS.

El objetivo no es moverlo ni renombrarlo automáticamente. Primero se inspecciona su situación real, se define el modelo de adopción y se documentan únicamente las excepciones que afecten la forma de trabajo.

## Antes de comenzar

Debes contar con acceso al proyecto existente, una ruta local conocida o remote confirmado, autorización para inspeccionar su estructura, un workspace elegido cuando corresponda e IA-DOS disponible por referencia remota o local.

La primera fase debe realizarse en modo lectura.

## Paso 1 — Identificar la realidad actual

Registra nombre, rutas, remotes, rama principal, working tree, repositorios relacionados, memoria existente, backlog, Exchange si existe, pipelines, despliegues, integraciones y dependencias de rutas relevantes.

No supongas que una carpeta equivale a un solo repositorio ni expongas secretos para describir su ubicación.

## Paso 2 — Clasificar la estructura existente

Mantén la estructura real cuando funcione. No separes automáticamente implementación y documentación, no muevas proyectos por estética y evalúa el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md) antes de crear memoria adicional.

Si existen varios repositorios o fuentes cuya relación no puede determinarse, detente antes de escribir y devuelve la ambigüedad al Cycle Owner.

## Paso 3 — Elegir el modelo de adopción

IA-DOS acepta repositorios separados, monorepos, rutas independientes u otras topologías claras.

Exchange puede vivir como recurso hermano, subdirectorio, carpeta sincronizada, repositorio independiente o no existir.

La topología elegida debe preservar historia, accesos y rutas reales. No necesita coincidir con un ejemplo.

## Paso 4 — Incorporar la implementación sin alterar su historia

Cuando el repositorio ya existe:

- no ejecutes `git init` nuevamente;
- no reemplaces remotes;
- no cambies la rama principal;
- no hagas commits automáticos;
- no muevas archivos para normalizar estructura sin una tarea específica;
- no elimines documentación antes de comprender su autoridad.

## Paso 5 — Evaluar el Memory Bootstrap Gate

Antes de delegar una unidad que dependa de historia o decisiones previas pregunta si puede ejecutarse correctamente sin reconstruir conocimiento relevante desde conversaciones.

- `PASS`: continúa.
- `BOOTSTRAP REQUIRED`: crea o conecta sólo el checkpoint durable mínimo.

## Paso 6 — Crear o conectar la memoria, cuando corresponda

Si ya existe memoria durable, conserva sus rutas cuando sean claras y no la renombres sólo para coincidir con el starter actual.

Si debe crearse una Wiki Markdown nueva, usa `templates/wiki-starter/` y [Crear o conectar la memoria durable](bootstrap-llm-wiki.md).

## Paso 7 — Evaluar Exchange por separado

La necesidad de Exchange no se deriva de tener una Wiki, varias conversaciones o muchas tareas.

Úsalo sólo cuando una pasarela de archivos Markdown entre Conversation Agent y Code Agent aporte valor.

Si ya existe un mecanismo equivalente:

- conserva su historia;
- identifica si es realmente una pasarela, backlog, memoria u otra cosa;
- no migres o renombres artefactos por estética;
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

- [ ] la historia Git fue preservada;
- [ ] los remotes no fueron modificados sin autorización;
- [ ] no se movieron archivos por normalización estética;
- [ ] las fuentes de verdad relevantes están identificadas;
- [ ] el Memory Bootstrap Gate fue evaluado cuando correspondía;
- [ ] la memoria existente fue preservada o el starter vigente se utilizó para una Wiki nueva;
- [ ] Exchange, si existe, se mantiene como pasarela pasiva y no como backlog, memoria o generador de identidad;
- [ ] no se asumió automatización inexistente;
- [ ] no se expusieron secretos;
- [ ] las rutas reales fueron reportadas.

## Condiciones de detención

Detente cuando exista trabajo no identificado, remotes inesperados, recursos relacionados cuya función no se comprenda, riesgo de romper rutas o despliegues, contradicciones relevantes entre documentación e implementación o falta de autorización para escribir.

## Siguiente paso

Si el Memory Bootstrap Gate requiere memoria, crea o actualiza sólo el checkpoint mínimo.

Si se decidió utilizar Exchange, crea o conecta únicamente la pasarela.

Después vuelve a la Planning Task, Environment Preflight o Execution Task que originó la adopción. No conviertas la incorporación en un proyecto paralelo.

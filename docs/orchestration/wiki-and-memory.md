# `90 — Wiki y memoria`

`90 — Wiki y memoria` es un Conversation Space especializado para gobernar conocimiento durable cuando el proyecto necesita una conversación propia para síntesis, contradicciones o mantenimiento documental.

No es obligatorio para crear un checkpoint inicial ni es, por definición, el agente que escribe físicamente la Wiki.

## Rol conceptual

`90` debe comprender:

- el propósito de la memoria durable;
- su estructura vigente;
- qué recursos son autoridad para cada afirmación;
- qué conocimiento merece registrarse;
- cómo distinguir hechos, decisiones, propuestas, pendientes y desconocidos;
- qué información debe preservarse;
- qué contradicciones requieren revisión;
- qué páginas deben actualizarse para mantener el estado vigente.

## Relación con el Memory Bootstrap Gate

El [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md) puede requerir un checkpoint durable sin obligar a abrir `90`.

Cuando el conocimiento ya está confirmado y la actualización es pequeña, `00` u otro Conversation Space autorizado puede preparar directamente una tarea documental.

Abre `90` cuando el trabajo de memoria tenga suficiente entidad propia como para beneficiarse de contexto persistente especializado.

## Salidas de `90`

Cuando exista conocimiento durable que materializar, `90` puede producir:

- síntesis del conocimiento confirmado;
- fuentes o evidencia que lo respaldan;
- decisiones y estados aplicables;
- contradicciones o desconocidos;
- rutas que deberían cambiar;
- contenido que debe preservarse;
- una propuesta de actualización documental ejecutable.

`90` puede redactar contenido propuesto, pero no debe afirmar que la memoria fue modificada sin evidencia del recurso real.

## Relación con el Project Orchestrator

El Project Orchestrator integra la salida de `90`, confirma alcance y autoridad, y prepara una `Execution Task` documental o un perfil `Wiki Update Task` compatible con el contrato canónico.

```text
90 — Wiki y memoria
    sintetiza y gobierna conocimiento durable
        ↓
Cycle Owner / Project Orchestrator
    confirma alcance, autoridad y criterios
        ↓
Execution Task documental
```

En proyectos pequeños, `00 — Dirección y orquestación` puede cumplir directamente esta función mientras mantenga la separación entre razonamiento y materialización.

## Relación con el coding agent

Cuando un coding agent recibe una tarea autorizada sobre la Wiki:

1. inspecciona las páginas requeridas;
2. modifica únicamente las rutas autorizadas;
3. preserva información vigente;
4. mantiene Markdown portable y enlaces relativos;
5. valida YAML sólo cuando exista y corresponda;
6. revisa el diff;
7. realiza branch, commit o pull request sólo cuando estén autorizados;
8. devuelve un `Execution Report` con evidencia.

Una Execution Cell como `Wiki Sync` puede existir cuando la sincronización o mantenimiento físico es un flujo durable del proyecto. No se crea automáticamente por usar una Wiki.

## Límites

`90` y el Project Orchestrator no deben:

- convertir hipótesis en hechos;
- registrar decisiones no confirmadas como vigentes;
- confundir decisión aceptada con implementación;
- duplicar TASK/REPORT en la Wiki por defecto;
- usar la Wiki como backlog o log operacional;
- pedir una reorganización completa cuando basta una actualización pequeña;
- presentar una propuesta como cambio implementado;
- modificar recursos sin acceso y autorización explícitos.

El coding agent no resuelve contradicciones conceptuales por cuenta propia. Cuando una contradicción cambia el contenido que debería registrarse, se detiene y la devuelve al Cycle Owner.
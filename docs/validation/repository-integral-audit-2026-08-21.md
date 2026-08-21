# Auditoría integral del repositorio — 2026-08-21

## Propósito

Esta revisión vuelve a inspeccionar IA-DOS como un sistema documental completo después de la consolidación de Fase 6 y de las actualizaciones posteriores de roadmap, `AGENTS.md`, influencias de diseño y guía conversacional.

El objetivo no es declarar el método perfecto ni congelarlo. Es comprobar que las superficies vigentes del repositorio enseñen los mismos contratos y que los artefactos copiables no reintroduzcan modelos ya reemplazados.

## Baseline de entrada

```text
main
75105697dcfc5991cdcc567531b4fc29e2cc118b
```

Incluye los merges hasta PR #42.

## Cobertura

La revisión cubrió las superficies actuales del repositorio:

- archivos raíz y contratos públicos;
- `docs/foundations/`;
- `docs/orchestration/`;
- `docs/execution/`;
- `docs/getting-started/`;
- `docs/integrations/`;
- `docs/discoverability/`;
- `docs/validation/`;
- `prompts/`;
- `templates/`;
- `templates/wiki-starter/`;
- `bundles/`;
- `research/`;
- archivos comunitarios y legales.

Los bundles históricos se inspeccionaron para confirmar que estén marcados como históricos, pero **no se reescribieron** con contratos actuales porque su función es conservar trazabilidad de generaciones anteriores.

## Invariantes usados como referencia

```text
Persona responsable = dirección y aprobación final aplicable
Conversation Space = gobierno dentro de autoridad delegada
Execution Cell = continuidad de ejecución
Execution Task = contrato de una unidad
Execution Report = evidencia de ejecución
Memoria durable = responsabilidad funcional
LLM Wiki = memoria durable materializada cuando se adopta
Repository = implementación
Exchange = pasarela pasiva de archivos
```

Además:

- `00 — Dirección y orquestación` es la entrada canónica y no un dispatcher obligatorio;
- Conversation Spaces se abren bajo demanda;
- la política universal de conversaciones de Planning permanece abierta;
- una Execution Cell no se renueva por edad, tiempo o cantidad de tareas;
- cada Execution Task vuelve a declarar permisos;
- Memory Bootstrap Gate ocurre antes de una Planning/Execution Task que dependa de historia chat-only;
- Environment Preflight precede escritura cuando readiness indispensable es desconocido;
- sólo `LISTO PARA EJECUCIÓN` habilita aprobar o reanudar escritura;
- Execution Resume sólo aplica si objetivo, alcance, autoridad, seguridad y arquitectura siguen sin cambios;
- Execution Report no selecciona decisión de gobierno ni memoria posterior;
- Exchange no define artefactos, IDs, filenames, templates, estados, permisos, backlog, memoria, decisiones o workflow.

## Hallazgos reales

### 1. Mezcla entre Execution Report y memoria

Persistían documentos y prompts que pedían al coding agent:

- `Conocimiento potencialmente durable`;
- actualización durable recomendada;
- siguiente acción.

Esto contradecía el contrato final de Execution Report como evidencia únicamente.

### 2. Sesiones de ejecución forzadas por resultado

Varias plantillas de Planning e Implementation Plan exigían abrir una sesión de ejecución independiente después de cada plan.

Eso contradecía `Execution Cell`, cuyo propósito es reutilizar continuidad de ejecución mientras siga respondiendo bien.

### 3. Readiness y Resume desactualizados

Persistían:

- estado `LISTO` en vez de `LISTO PARA EJECUCIÓN`;
- `Agent Session` en ejecución;
- condiciones de Resume que omitían `autoridad` entre las fronteras que deben permanecer sin cambios.

### 4. Gates incompletos

Varias rutas rápidas enseñaban únicamente `Planning` versus `Execution` y podían omitir:

- Memory Bootstrap Gate;
- Environment Preflight.

### 5. Terminología histórica presentada como vigente

Persistían referencias operativas a:

- `Launch Mode`;
- `Exchange Protocol v0`;
- `Context Pack` como concepto normal del método actual.

Estos términos se conservaron sólo como compatibilidad histórica donde aporta, pero se retiraron de contratos vigentes.

### 6. Cycle Owner sin frontera humana suficientemente explícita

Algunos documentos podían interpretarse como si el Cycle Owner reemplazara la aprobación final de la persona.

Se reforzó que el Cycle Owner gobierna dentro de autoridad delegada y que la persona responsable conserva aprobación final sobre dirección, autoridad, riesgo e impactos relevantes.

### 7. LLM Wiki y memoria durable confladas

Persistían formulaciones donde `Wiki` y `memoria durable` eran sinónimos físicos.

Se consolidó:

```text
memoria durable
= responsabilidad funcional

LLM Wiki
= una materialización portable y navegable
```

### 8. Exchange tratado como posible backlog

Una plantilla `AGENTS.md` incluía Exchange como candidato a sistema de trabajo pendiente.

Se corrigió: Exchange puede conservar archivos intercambiados, pero backlog y seguimiento pertenecen a otro sistema elegido por el proyecto.

### 9. Discoverability desactualizada

La identidad pública todavía exponía componentes y secuencias anteriores. Se actualizó para reflejar memoria, readiness, Planning, Execution Cells, Exchange pasivo y responsabilidad humana.

### 10. Current Offline Pack atrasado

El bundle vigente declaraba baseline de Fase 6 y no contenía todas las correcciones posteriores.

Se regeneró para `v0.1.0-alpha.3 — auditoría integral 2026-08-21`.

## Correcciones aplicadas

La revisión actualizó contratos en:

- fuentes de verdad y terminología;
- propósito, modelo operativo, memoria portable y checklists;
- routing, cycle ownership, fast lane, flujo concreto y handoff técnico;
- onboarding nuevo y existente;
- coding agents, readiness y Resume;
- identidad pública y comprensión por LLMs;
- prompts de inicialización, workspace, ejecución y Wiki;
- templates de AGENTS, roles, Planning, Implementation Plan, Preflight, Resume y Specialist Handoff;
- README;
- Current Offline Pack.

## Históricos preservados

No se reescribieron como método actual:

- `bundles/ia-dos-project-orchestrator-pack.md`;
- `bundles/ia-dos-agent-role-and-artifact-loop-addon.md`;
- `bundles/ia-dos-fast-planning-addon.md`;
- `bundles/ia-dos-typed-compact-addon.md`.

Sus encabezados ya advierten que son históricos y no deben utilizarse para nuevos onboardings.

## Criterio de cierre

La auditoría se considera cerrable cuando el diff final confirme que:

- no hay variantes incompatibles de Execution Report;
- ninguna plantilla vigente obliga a una sesión de ejecución por tarea;
- Planning session se mantiene opcional/lógica;
- readiness usa estados canónicos;
- Resume conserva objetivo, alcance, autoridad, seguridad y arquitectura;
- Memory Bootstrap y Preflight no pueden saltarse en rutas rápidas;
- LLM Wiki no es topología obligatoria;
- Exchange sigue pasivo;
- responsabilidad humana está visible;
- Current Offline Pack reproduce los contratos vigentes;
- los bundles históricos permanecen aislados;
- no hay enlaces o rutas rotas introducidos por la revisión.

## Relación con validaciones anteriores

`end-to-end-onboarding-validation.md` y `final-integral-review.md` documentan el estado de la consolidación de Fase 6 en su momento.

Esta auditoría no invalida su valor histórico, pero **supersede su conclusión de coherencia final como evaluación del estado actual del repositorio**. Las regresiones encontradas muestran por qué las validaciones deben tratarse como evidencia fechada, no como garantía permanente.

## Estado

```text
AUDITORÍA EN CORRECCIÓN
```

Este estado debe cambiar a `PASS` sólo después de revisar el diff completo de la branch, resolver feedback válido de revisión y comprobar el conjunto final contra los invariantes anteriores.

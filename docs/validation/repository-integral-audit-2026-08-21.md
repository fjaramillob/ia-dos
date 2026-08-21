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

También se distinguió explícitamente entre:

- archivos revisados y corregidos;
- archivos revisados que no requerían cambios;
- artefactos históricos que deben conservar su contenido original con advertencia de vigencia.

## Invariantes usados como referencia

```text
Persona responsable = dirección y aprobación final aplicable
Conversation Space   = gobierno dentro de autoridad delegada
Execution Cell       = continuidad de ejecución
Execution Task       = contrato de una unidad
Execution Report     = evidencia de ejecución
Memoria durable      = responsabilidad funcional
LLM Wiki             = materialización durable, portable y navegable
Repository           = implementación
Exchange             = pasarela pasiva de archivos
```

Además:

- `00 — Dirección y orquestación` es la entrada canónica y no un dispatcher obligatorio;
- Conversation Spaces se abren bajo demanda;
- la política universal de conversaciones de Planning permanece abierta;
- una Execution Cell no se renueva por edad, tiempo o cantidad de tareas;
- cada Execution Task vuelve a declarar permisos;
- Memory Bootstrap Gate ocurre antes de una Planning/Execution Task que dependa de historia chat-only;
- `BOOTSTRAP REQUIRED` bloquea la unidad dependiente original, no la unidad mínima necesaria para materializar el checkpoint;
- Environment Preflight precede escritura cuando readiness indispensable es desconocido;
- sólo `LISTO PARA EJECUCIÓN` habilita aprobar o reanudar escritura;
- Execution Resume sólo aplica si objetivo, alcance, autoridad, seguridad y arquitectura siguen sin cambios;
- Execution Report no selecciona decisión de gobierno ni memoria posterior;
- el Coding Agent — Planning no asigna Task ID a una Execution Task candidata;
- la persona responsable conserva aprobación final cuando cambian dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante;
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

La segunda pasada encontró el mismo problema en `topic-routing-registry.md`, que también fue corregido.

### 5. Terminología histórica presentada como vigente

Persistían referencias operativas a:

- `Launch Mode`;
- `Exchange Protocol v0`;
- `Context Pack` como concepto normal del método actual.

Estos términos se conservaron sólo como historia o compatibilidad donde aporta, pero se retiraron de contratos vigentes.

### 6. Cycle Owner sin frontera humana suficientemente explícita

Algunos documentos podían interpretarse como si el Cycle Owner reemplazara la aprobación final de la persona.

Se reforzó que el Cycle Owner gobierna dentro de autoridad delegada y que la persona responsable conserva aprobación final cuando una decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

### 7. LLM Wiki y memoria durable confladas

Persistían formulaciones donde `Wiki` y `memoria durable` eran sinónimos físicos.

Se consolidó:

```text
memoria durable
= responsabilidad funcional

LLM Wiki
= materialización durable, portable y navegable
  de esa memoria para humanos y agentes
```

### 8. Exchange tratado como posible backlog

Una plantilla `AGENTS.md` incluía Exchange como candidato a sistema de trabajo pendiente.

Se corrigió: Exchange puede conservar archivos intercambiados, pero backlog y seguimiento pertenecen a otro sistema elegido por el proyecto.

### 9. Discoverability desactualizada

La identidad pública todavía exponía componentes y secuencias anteriores. Se actualizó para reflejar memoria, readiness, Planning, Execution Cells, Exchange pasivo y responsabilidad humana.

### 10. Current Offline Pack atrasado

El bundle vigente declaraba baseline de Fase 6 y no contenía todas las correcciones posteriores.

Se regeneró para `v0.1.0-alpha.3 — auditoría integral 2026-08-21` y se volvió a contrastar contra los invariantes durante las rondas de revisión.

### 11. Instalación local imponía topología de proyecto

La guía y el prompt de instalación de IA-DOS todavía mostraban como resultado esperado:

```text
00-ia-dos/
<proyecto>-app/
<proyecto>-wiki/
```

Eso podía convertir una instalación de referencia del framework en una decisión accidental sobre la topología del proyecto.

Se corrigió: instalar IA-DOS sólo crea, cuando está autorizado, una referencia local equivalente a:

```text
<workspace>/00-ia-dos/
```

La creación o reorganización de app, LLM Wiki, Exchange u otros recursos pertenece a tareas separadas del proyecto.

### 12. Validaciones históricas podían leerse como certificación vigente

`end-to-end-onboarding-validation.md` y `final-integral-review.md` conservaban títulos y conclusiones de `PASS` sin una advertencia visible de que describían el baseline de Fase 6.

La auditoría actual demostró que una validación pasada no puede actuar como garantía permanente.

Ambos documentos se preservaron como evidencia histórica y ahora enlazan esta auditoría como revisión más reciente.

### 13. Tipo `WIKI` podía interpretarse como autorización implícita

El registro de tipos de ejecución describía `WIKI` como actualización de memoria y mencionaba la necesidad de actualizar memoria entre los campos influenciados por el tipo.

Se aclaró que el tipo clasifica el trabajo, pero **no concede autorización**: la propia Execution Task debe delimitar explícitamente conocimiento, rutas y permisos de una actualización durable.

### 14. Circularidad entre Memory Bootstrap Gate y Execution Task

La primera versión corregida de `Execution Task` exigía:

```text
Memory Bootstrap Gate = PASS | NO APLICA
```

Eso introducía una circularidad: cuando el gate devolvía `BOOTSTRAP REQUIRED`, hacía falta persistir memoria antes de la unidad original, pero el contrato parecía prohibir emitir la propia Execution Task documental necesaria para materializar ese checkpoint.

La semántica consolidada queda:

```text
unidad A depende de memoria chat-only
→ BOOTSTRAP REQUIRED
→ unidad A queda bloqueada
→ Execution Task B sólo materializa el checkpoint mínimo
→ Execution Report B
→ revisión
→ se reevalúa el gate de A
→ PASS
→ A puede emitirse
```

La tarea B no puede mezclar la unidad A ni fingir que el gate original ya está en `PASS`.

### 15. Contrato incompleto de `Coding Agent — Planning`

Algunas superficies definían el rol sólo como:

```text
Planning Task
→ Coding Agent — Planning
→ Implementation Plan
```

pero el mismo rol también recibe Preflight.

Se consolidaron ambos pares válidos de solo lectura:

```text
Planning Task
→ Coding Agent — Planning
→ Implementation Plan

Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

Planning y Preflight comparten rol, no artefacto ni salida.

### 16. Propagación incompleta de la excepción de Memory Bootstrap

Después de corregir el contrato canónico, varias superficies autónomas todavía resumían `BOOTSTRAP REQUIRED` como “persistir primero” sin enseñar la unidad separada, el fuera de alcance, la revisión del reporte y la reevaluación del gate.

La revisión de pull request detectó variantes en:

- initializer del Project Orchestrator;
- onboarding de proyecto nuevo;
- onboarding de proyecto existente;
- handoff técnico;
- rutas de orquestación;
- guía conversacional;
- prompt de incorporación de proyecto existente;
- guía de incorporación al workspace;
- Current Offline Pack.

Se propagó la misma semántica completa a todas esas superficies vigentes.

### 17. Frontera de aprobación humana no uniforme

Persistían dos reducciones de autoridad:

- algunas superficies omitían `cumplimiento`;
- otras reservaban sólo `datos sensibles`, mientras el contrato vigente reserva cambios sobre `datos` en general.

Se normalizó la frontera:

```text
dirección
+ autoridad
+ riesgo
+ coste
+ producción
+ datos
+ seguridad
+ cumplimiento
+ impacto relevante
```

### 18. Task ID asignado desde Planning

Varias superficies de Planning permitían o inducían al coding agent a crear la identidad de una Execution Task candidata.

Se consolidó:

```text
Coding Agent — Planning
→ propone la unidad
→ Task ID: PENDIENTE — ASIGNAR AL ADOPTAR

Conversation Agent / Cycle Owner
→ revisa y adopta la candidata
→ asigna Task ID
→ construye la Execution Task real
```

La regla se propagó a Implementation Plan, Planning Task completa/compacta, prompt de Planning, Project Start Planning Brief, prompt de incorporación existente y Current Offline Pack.

### 19. Paridad autónoma del Current Offline Pack

La revisión encontró que el pack offline podía quedar semánticamente detrás del repositorio aun cuando los contratos canónicos ya estuvieran corregidos.

Se verificó y sincronizó explícitamente en el pack:

- frontera humana completa;
- Memory Bootstrap separado;
- rol y salida de Environment Preflight;
- Execution Cells y autorización no acumulativa;
- Task ID pendiente para candidatas de Planning;
- Execution Report como evidencia;
- Exchange pasivo.

El pack sigue siendo artefacto de distribución, no segunda fuente canónica.

## Correcciones aplicadas

La revisión actualizó o volvió a sincronizar contratos en:

- `AGENTS.md`, `README.md`, `ORCHESTRATOR.md`, `ROADMAP.md` y `CHANGELOG.md`;
- fuentes de verdad, terminología, propósito, responsabilidades y modelo operativo;
- Memory Bootstrap Gate, memoria portable y checklists fundacionales;
- routing, cycle ownership, fast lane, flujo concreto, compresión y handoff técnico;
- onboarding nuevo, existente, workspace e instalación local;
- coding agents, tipos de ejecución, readiness y Resume;
- identidad pública y comprensión por LLMs;
- prompts de inicialización, instalación, workspace, Planning, Execution y Wiki;
- templates de AGENTS, roles, Planning, Implementation Plan, Preflight, Resume, Execution Task, Execution Report, Wiki Update Task y Specialist Handoff;
- Current Offline Pack;
- documentación de validación histórica y la propia evidencia de esta auditoría.

## Superficies revisadas sin corrección de contrato

Entre las superficies revisadas que no necesitaron cambios semánticos adicionales quedaron:

- `docs/integrations/` y `Capability Manifest`;
- `templates/adoption.template.yaml`;
- `templates/wiki-starter/` después de la consolidación previa;
- `docs/getting-started/bootstrap-exchange.md`;
- `docs/getting-started/bootstrap-llm-wiki.md`;
- `docs/getting-started/apply-starter-templates.md`;
- `research/design-influences.md`;
- `CONTRIBUTING.md`, `GOVERNANCE.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md`, `LICENSE` y la plantilla general de pull request.

Que un archivo no cambie no significa que haya quedado fuera de cobertura.

## Históricos preservados

No se reescribieron como método actual:

- `bundles/ia-dos-project-orchestrator-pack.md`;
- `bundles/ia-dos-agent-role-and-artifact-loop-addon.md`;
- `bundles/ia-dos-fast-planning-addon.md`;
- `bundles/ia-dos-typed-compact-addon.md`.

Sus encabezados ya advierten que son históricos y no deben utilizarse para nuevos onboardings.

Las validaciones de Fase 6 también se preservan como evidencia histórica, pero ahora están etiquetadas explícitamente para no competir con esta auditoría vigente.

## Revisión del pull request

La PR #43 se revisó de forma iterativa contra heads exactos. Cada hallazgo válido se corrigió, se propagó a superficies hermanas cuando correspondía y su review thread quedó resuelto antes de solicitar una nueva revisión.

La última revisión contractual se ejecutó sobre:

```text
07d90ab7f1b684af1a7c435689820acfc114b2d5
```

Codex devolvió:

```text
Didn't find any major issues.
```

No quedaron nuevos review threads abiertos en ese head.

Los hallazgos automáticos fueron tratados como evidencia de revisión, no como autoridad final: cada uno se contrastó contra los contratos canónicos antes de modificar el repositorio.

## Limitaciones de validación

Esta auditoría es integral respecto de las superficies documentales y contractuales del repositorio bajo el baseline indicado, pero no debe interpretarse como garantía permanente frente a cambios futuros.

Además:

- el repositorio no tiene workflows ni status checks configurados para esta PR, por lo que no existe una suite CI que pueda declararse ejecutada;
- no se ejecutó un clone local ni un link checker mecánico desde el entorno de esta revisión porque esa capacidad no estuvo disponible de forma fiable;
- enlaces y rutas afectadas se revisaron desde las fuentes conectadas y el diff, pero no se afirma una validación mecánica local inexistente;
- los bundles históricos se preservaron deliberadamente y no forman parte del contrato operativo vigente.

## Criterio de cierre

El diff contractual revisado confirma que:

- no hay variantes vigentes conocidas de Execution Report que mezclen evidencia con decisión o memoria posterior;
- ninguna plantilla vigente revisada obliga a una sesión de ejecución por tarea;
- Planning session se mantiene opcional/lógica;
- readiness usa estados canónicos;
- Resume conserva objetivo, alcance, autoridad, seguridad y arquitectura;
- Memory Bootstrap y Preflight no se omiten en las rutas operativas revisadas;
- `BOOTSTRAP REQUIRED` bloquea la unidad dependiente pero permite la unidad mínima separada de persistencia del checkpoint;
- una candidata de Planning deja el Task ID pendiente para el Conversation Agent / Cycle Owner;
- LLM Wiki no es topología obligatoria;
- instalar IA-DOS no crea topología del proyecto;
- Exchange sigue pasivo;
- responsabilidad humana está visible y usa una frontera uniforme;
- Current Offline Pack reproduce los contratos vigentes revisados;
- los bundles y validaciones históricos permanecen aislados de la operación actual.

## Relación con validaciones anteriores

`end-to-end-onboarding-validation.md` y `final-integral-review.md` documentan el estado de la consolidación de Fase 6 en su momento.

Esta auditoría no invalida su valor histórico, pero **reemplaza su conclusión de coherencia final como evaluación del estado actual del repositorio**. Las regresiones encontradas muestran por qué las validaciones deben tratarse como evidencia fechada, no como garantía permanente.

## Estado

```text
PASS
```

La auditoría queda cerrada para el baseline revisado. La conclusión significa que, dentro de la cobertura y limitaciones declaradas, las superficies vigentes revisadas convergen al mismo modelo operacional y que la última revisión contractual del pull request no encontró nuevos problemas mayores.

Cualquier modificación futura de contratos transversales debe volver a evaluar sus representaciones en documentación canónica, prompts, templates, onboarding y Current Offline Pack; este `PASS` es evidencia fechada, no una certificación perpetua.

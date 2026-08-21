# Adoptar un proyecto existente desde la capa conversacional

Este recorrido comienza en conversación y pasa al entorno técnico cuando hace falta inspeccionar o modificar artefactos reales.

## 1. Inicializar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md` y entrega las fuentes disponibles: repositorio, LLM Wiki o memoria, documentación, reportes, enlaces y restricciones.

## 2. Confirmar el escenario

Clasifica el producto objetivo como existente cuando el propio producto tiene evidencia de implementación, usuarios, despliegue, infraestructura, integraciones o documentación técnica vigente.

Una migración, reconstrucción o producto sucesor es un atributo, no un tercer escenario.

## 3. Abrir `00 — Dirección y orquestación`

Para un producto existente, `00` trabaja en modo `descubrimiento y adopción` y comprende sólo lo necesario para orientar la siguiente unidad:

- qué producto existe;
- qué está implementado, parcial, planificado, deprecado o desconocido;
- qué fuentes y repositorios participan;
- qué decisiones siguen vigentes;
- qué problemas o riesgos son conocidos;
- cuál es la prioridad actual.

No describas como real algo que no tenga evidencia.

## 4. Organizar conversaciones bajo demanda

Usa `docs/orchestration/topic-routing-registry.md` como única lista normativa de Conversation Spaces.

`00` debe indicar si basta continuar allí o si la brecha dominante requiere un espacio especializado con contexto persistente propio.

No abras `90`, `30` ni otro espacio por rutina. Un coding agent no requiere un Conversation Space adicional sólo para ejecutar una tarea.

## 5. Evaluar memoria antes de depender de historia

Antes de emitir una Planning Task o Execution Task que dependa de decisiones, estado o contexto previo, evalúa [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md).

```text
PASS
→ la unidad evaluada puede continuar sin reconstruir conversaciones

BOOTSTRAP REQUIRED
→ la unidad evaluada queda bloqueada
→ emite una Execution Task separada cuyo único resultado sea persistir el checkpoint durable mínimo
→ deja la unidad original explícitamente fuera de alcance
→ revisa el Execution Report del bootstrap
→ reevalúa el gate de la unidad original
```

La tarea de bootstrap declara explícitamente que responde a `BOOTSTRAP REQUIRED`; no finge `PASS` ni ejecuta la unidad original que busca desbloquear.

No reconstruyas toda la historia. Captura sólo estado vigente, decisiones que condicionan la siguiente unidad, fuentes de verdad y desconocidos relevantes.

Una LLM Wiki separada no es obligatoria.

## 6. Obtener evidencia o readiness cuando falten

Después de satisfacer el gate de memoria —o cuando la unidad actual sea precisamente el checkpoint de bootstrap— identifica qué falta realmente:

- falta inspección o diseño técnico → `Planning Task` de solo lectura respecto del proyecto/entorno;
- falta comprobar runtime, servicio, acceso, secreto o conectividad indispensable → `Environment Preflight` de solo lectura respecto del entorno;
- unidad ya definida y entorno listo → `Execution Task`.

Planning y Preflight no modifican artefactos, datos, configuración ni estado del proyecto o entorno inspeccionado. Cuando la Task declara `Output Delivery`, sí pueden materializar **únicamente su propio artefacto de salida** en el destino autorizado: `Implementation Plan` o `Environment Readiness Report`. Esa excepción no convierte el rol en Execution ni concede escritura adicional.

El Preflight usa el contrato tipado:

```text
Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

El resultado vuelve al mismo Cycle Owner. No abras otro Conversation Space sólo para ejecutar la inspección técnica.

Sólo un `Environment Readiness Report` con `LISTO PARA EJECUCIÓN` permite considerar aprobación o reanudación de escritura sobre el proyecto/entorno. La materialización del propio reporte autorizado no constituye esa autorización posterior.

## 7. Preparar el entorno cuando corresponda

La instalación local no es requisito previo del onboarding. Úsala cuando la siguiente tarea necesite acceso real a repositorios, archivos, Git o herramientas locales.

Guías opcionales:

- [Preparar el workspace local](workspace-setup.md)
- [Instalar IA-DOS](install-ia-dos.md)
- [Incorporar el proyecto existente](incorporate-existing-project-workspace.md)
- [Crear o revisar la memoria durable](bootstrap-llm-wiki.md)
- [Preparar el handoff de ejecución](execution-handoff.md)

No muevas, renombres ni reorganices un proyecto existente sólo para cumplir una estructura recomendada.

## 8. Ejecutar y retornar

```text
Conversation Space / Cycle Owner
→ Execution Task
→ Execution Cell adecuada o entorno disponible
→ Coding Agent — Execution
→ Execution Report
→ mismo Cycle Owner
→ revisión
→ persona responsable cuando la decisión requiera aprobación humana
```

Una Execution Task no obliga a crear una conversación nueva. Reutiliza una Execution Cell activa cuando corresponda.

Cada tarea vuelve a declarar alcance, autoridad y permisos. La continuidad conversacional no hereda autorizaciones anteriores.

Si el Execution Report corresponde a un memory bootstrap, primero reevalúa el gate de la unidad original; no la autoriza automáticamente.

Exchange puede utilizarse como pasarela pasiva opcional para `.md`. No sustituye backlog, memoria o implementación y no define artefactos, IDs o estados.

Sólo vuelve a `00` cuando aparezca una reorientación real.

## Primera unidad recomendada

Comienza con un resultado de bajo riesgo y verificable, por ejemplo:

- inspeccionar una incertidumbre técnica concreta;
- documentar un flujo existente;
- corregir un bug acotado;
- añadir una prueba;
- actualizar una funcionalidad pequeña;
- verificar una integración.

No conviertas la adopción en una auditoría integral antes de poder avanzar.

## Memoria durable

La memoria adoptada distingue conocimiento vigente de historia operacional.

No copies conversaciones completas ni trates un Execution Report como estado oficial sin revisión.

Si se crea una LLM Wiki Markdown nueva, usa el starter vigente y expándelo sólo cuando exista conocimiento durable real.

## Responsabilidad

El Cycle Owner gobierna dentro de la autoridad delegada. La persona responsable conserva la aprobación final cuando cambian dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

El coding agent no aprueba su propio resultado ni inicia otra unidad.

## Resultado esperado

- producto clasificado con evidencia;
- `00 — Dirección y orquestación` usado en modo `descubrimiento y adopción`;
- estado real comprendido sin inventar historia;
- Conversation Spaces bajo demanda;
- Memory Bootstrap Gate satisfecho antes de depender de contexto histórico;
- `BOOTSTRAP REQUIRED` resuelto mediante una unidad de checkpoint separada antes de retomar la unidad original;
- Planning o Preflight usado sólo cuando corresponde;
- Planning/Preflight conservan solo lectura del proyecto/entorno y materializan únicamente su output cuando `Output Delivery` lo autoriza;
- Preflight tipado como `Environment Preflight → Coding Agent — Planning → Environment Readiness Report`;
- primera Execution Task acotada cuando la unidad está lista;
- Execution Cell reutilizada cuando corresponda;
- evidencia devuelta al Cycle Owner;
- responsabilidad humana preservada;
- memoria durable creada o actualizada progresivamente.

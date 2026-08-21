# Iniciar un proyecto nuevo desde la capa conversacional

Este recorrido comienza en conversación. La preparación técnica aparece después, cuando una unidad necesita repositorios, archivos, Git, servicios o un coding agent.

## 1. Inicializar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md` y entrega una descripción inicial y las fuentes disponibles.

## 2. Confirmar el escenario

Clasifica el producto objetivo como nuevo. Una migración, reconstrucción o sistema anterior usado como referencia no cambia por sí solo esta clasificación.

## 3. Abrir `00 — Dirección y orquestación`

Para un producto nuevo, `00` trabaja en modo `definición inicial` y captura sólo lo necesario para avanzar:

- propósito;
- usuario principal;
- problema central;
- promesa de valor;
- principios o restricciones no negociables;
- prioridad o primer resultado;
- límites y riesgos relevantes.

La primera respuesta debe ser breve y seguir como base:

1. Lo que entendí.
2. Prioridad propuesta.
3. Qué falta resolver ahora.
4. Organización de conversaciones sólo si aporta.
5. Cómo trabajaremos.
6. Tu siguiente acción.

## 4. Conversation Spaces bajo demanda

Usa `docs/orchestration/topic-routing-registry.md` como lista normativa de Conversation Spaces.

`00` debe indicar si basta seguir allí o si la brecha dominante justifica abrir un único espacio especializado con contexto persistente propio.

No abras espacios como secuencia automática. No abras `30` sólo porque exista trabajo para un coding agent; ejecución conversacional y Execution Cells son conceptos distintos.

## 5. Cuando la persona quiere avanzar

Expresiones como `avancemos`, `empecemos`, `sigamos` o equivalentes no activan una fase especial.

El Project Orchestrator identifica el siguiente resultado verificable y evalúa:

```text
1. ¿El resultado está suficientemente definido y acotado?
2. Si depende de historia previa, ¿el conocimiento necesario ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿corresponde Planning?
```

Según el caso:

- conocimiento necesario sólo en conversaciones → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección o diseño → `Planning Task` de solo lectura;
- unidad definida + memoria suficiente + entorno listo → `Execution Task`;
- decisión humana indispensable → deriva sólo esa decisión;
- reorientación → `00`.

No fuerces una Execution Task sólo porque la persona manifestó intención de avanzar.

## 6. Memory Bootstrap Gate

Antes de una Planning Task o Execution Task que dependa de historia, pregunta:

> ¿La siguiente unidad puede ejecutarse correctamente sin depender de conocimiento relevante que exista sólo en conversaciones efímeras?

```text
PASS
→ continúa sin documentación adicional

BOOTSTRAP REQUIRED
→ la unidad evaluada queda bloqueada
→ emite una Execution Task separada cuyo único resultado sea persistir el checkpoint durable mínimo
→ deja la unidad original explícitamente fuera de alcance
→ revisa el Execution Report del bootstrap
→ reevalúa el gate de la unidad original
```

La tarea de bootstrap no finge `PASS` y no puede ejecutar la unidad original que busca desbloquear. Declara explícitamente que responde a `BOOTSTRAP REQUIRED`.

Una LLM Wiki separada no es obligatoria y `90 — Wiki y memoria` no debe abrirse por rutina.

## 7. Preparar el entorno cuando corresponda

La instalación local no es requisito previo del onboarding.

Cuando la siguiente unidad necesite acceso real, utiliza sólo las guías aplicables:

- [Preparar el workspace local](workspace-setup.md)
- [Instalar IA-DOS](install-ia-dos.md)
- [Crear el proyecto en el workspace](create-new-project-workspace.md)
- [Crear o conectar la memoria durable](bootstrap-llm-wiki.md)
- [Preparar el handoff técnico](execution-handoff.md)

No impongas una topología física cuando el proyecto no la necesita.

## 8. Ejecutar y retornar

```text
Conversation Space / Cycle Owner
→ Execution Task
→ Execution Cell adecuada o entorno disponible
→ coding agent
→ cambios + verificaciones
→ Execution Report
→ mismo Cycle Owner
→ revisión
```

Una `Execution Task` no implica una conversación nueva. Si existe una Execution Cell adecuada y su conversación activa sigue respondiendo bien, reutilízala.

Cada tarea vuelve a declarar permisos, alcance, criterios y condiciones de detención.

Exchange puede utilizarse como pasarela pasiva opcional de `.md`. No cambia contratos, IDs, estados o permisos.

## 9. Responsabilidad y revisión

El Cycle Owner gobierna dentro de la autoridad delegada. La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

El `Execution Report` aporta evidencia mediante:

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El coding agent no aprueba su propio resultado, no decide la siguiente unidad y no consolida memoria durable por defecto.

Si el reporte corresponde a un memory bootstrap, su revisión no habilita automáticamente la unidad original: primero se reevalúa su Memory Bootstrap Gate.

## Resultado esperado

- dirección inicial suficiente;
- `00 — Dirección y orquestación` como entrada canónica;
- Conversation Spaces bajo demanda;
- ningún `Launch Mode` o fase artificial;
- Memory Bootstrap Gate aplicado cuando la unidad dependa de historia conversacional;
- `BOOTSTRAP REQUIRED` resuelto mediante una unidad de checkpoint separada antes de retomar la unidad original;
- Environment Preflight usado cuando readiness indispensable sea desconocido;
- Planning Task sólo cuando reduzca incertidumbre real;
- Execution Task acotada cuando la unidad esté lista;
- Execution Cell reutilizada cuando corresponda;
- evidencia devuelta al Cycle Owner;
- memoria durable construida progresivamente sólo cuando aporte.

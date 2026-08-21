# Handoff entre Conversation Space y coding agent

Este flujo convierte una necesidad confirmada en inspección, planificación o ejecución acotada, verificable y trazable.

Consulta según corresponda:

- [Registro de tópicos conversacionales](../orchestration/topic-routing-registry.md);
- [Propiedad y retorno del ciclo](../orchestration/cycle-ownership.md);
- [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md);
- [Readiness del entorno y reanudación](../execution/environment-readiness-and-resume.md);
- [Tipado de artefactos](../orchestration/typed-artifact-routing.md);
- [Autoridad de fuentes, artefactos y entornos](../execution/source-and-artifact-authority.md).

## Flujo

```text
Conversation Space
→ resultado esperado + Cycle Owner
→ Memory Bootstrap Gate cuando depende de historia
→ Environment Preflight cuando readiness es desconocido
→ Planning Task cuando falta inspección/diseño
   o Execution Task cuando la unidad está lista
→ coding agent
→ retorno tipado
→ mismo Cycle Owner
→ revisión y decisión según autoridad
```

`00` no es una parada obligatoria.

## 1. Confirmar propiedad y destinos

Antes de delegar, declara:

- resultado esperado;
- Cycle Owner;
- destino del artefacto de retorno;
- espacio de escalamiento cuando corresponda.

El Cycle Owner actúa dentro de la autoridad delegada. La persona responsable conserva la aprobación final cuando la decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

## 2. Evaluar memoria

Antes de una Planning Task o Execution Task que dependa de historia previa, aplica:

> ¿La siguiente unidad puede ejecutarse correctamente sin depender de conocimiento relevante que exista sólo en conversaciones efímeras?

```text
PASS
→ continúa con la unidad evaluada

BOOTSTRAP REQUIRED
→ bloquea la unidad evaluada
→ emite una Execution Task separada cuyo único resultado sea persistir el checkpoint durable mínimo
→ deja la unidad original fuera de alcance
→ revisa el Execution Report del bootstrap
→ reevalúa el gate de la unidad original
```

La tarea de bootstrap declara explícitamente que responde a `BOOTSTRAP REQUIRED`; no finge `PASS` ni ejecuta la unidad que busca desbloquear.

No crees una LLM Wiki completa por ceremonia.

## 3. Evaluar readiness

Si una Execution Task depende de runtime, herramienta, servicio, acceso, secreto o conectividad indispensable no comprobados, prepara `Environment Preflight` en solo lectura.

Contrato tipado:

```text
Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

Sólo `LISTO PARA EJECUCIÓN` habilita aprobar o reanudar escritura. El readiness report no concede escritura por sí mismo.

## 4. Decidir Planning o Execution

Pregunta:

```text
¿El resultado está suficientemente definido, es pequeño y puede ejecutarse
con seguridad sin inspección o diseño técnico adicional?
```

- sí → Execution Task;
- no por falta de inspección/diseño → Planning Task;
- no por decisión humana indispensable → deriva sólo esa decisión;
- no por reorientación → escala a `00`.

Una unidad ordinaria dependiente de memoria previa sólo llega a este gate después de `Memory Bootstrap Gate = PASS`. La unidad separada de checkpoint es la excepción explícita descrita arriba.

## 5. Planning Task

La Planning Task:

- es de solo lectura;
- resuelve una incertidumbre técnica dominante;
- declara fuentes, autoridad y límites;
- devuelve un `Implementation Plan` al Cycle Owner;
- no autoriza escritura ni ejecución.

Un identificador lógico de planning no obliga a crear una conversación nueva por tarea.

## 6. Revisar el Implementation Plan

El Cycle Owner compara evidencia, hechos, inferencias, riesgos, dependencias y tamaño de la primera unidad propuesta.

Cuando la primera unidad sea segura, prepara o valida una `Execution Task` candidata y obtiene la autorización humana aplicable.

Plan producido no equivale a plan aprobado ni a ejecución autorizada.

## 7. Execution Task

Usa la plantilla compacta o completa según la complejidad.

Debe declarar:

- objetivo único;
- Cycle Owner y destino;
- Execution Cell o sesión cuando corresponda;
- contexto durable estrictamente necesario;
- fuentes y autoridad;
- alcance y fuera de alcance;
- zonas autorizadas;
- capacidades y acciones externas autorizadas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención.

Antes de ejecutar, confirma que pueda completarse, verificarse y reportarse como una sola unidad.

Una Execution Cell activa se reutiliza mientras siga respondiendo bien. No abras una conversación nueva sólo porque cambia la tarea. Cada tarea vuelve a declarar sus permisos.

## 8. Ejecutar

El coding agent:

1. valida rol y tarea;
2. lee instrucciones locales aplicables;
3. inspecciona el estado real antes de escribir;
4. modifica sólo lo autorizado;
5. ejecuta verificaciones;
6. revisa el diff;
7. devuelve un `Execution Report` al destino indicado.

## 9. Revisar el Execution Report

El reporte utiliza:

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El Cycle Owner revisa objetivo, alcance, evidencia, verificaciones, autorizaciones, desviaciones y pendientes del alcance original.

El coding agent no aprueba su propio resultado, no selecciona la siguiente acción y no consolida memoria durable por defecto.

Después de revisar la evidencia, la autoridad correspondiente decide cierre, corrección, reversión, transferencia, escalamiento o siguiente unidad. Separadamente se evalúa si hechos nuevos merecen consolidación durable.

Si el reporte corresponde a un memory bootstrap, primero reevalúa el gate de la unidad original; no la autoriza automáticamente.

## 10. Cerrar o continuar

Al cerrar:

- la implementación permanece en el artefacto técnico real;
- la evidencia permanece en Report/diff/PR u otro mecanismo;
- la memoria durable se actualiza sólo con conocimiento confirmado y mediante una acción autorizada;
- Exchange, si existe, sólo conserva o transporta los `.md` intercambiados;
- `00` recibe únicamente reorientación real.

## Rechaza el cierre cuando

- falta autoridad o destino;
- una Planning Task produjo cambios;
- un plan se presenta como implementación;
- readiness indispensable sigue `NO LISTO` o `DESCONOCIDO`;
- una unidad ordinaria depende de memoria chat-only sin haber resuelto `BOOTSTRAP REQUIRED`;
- la Execution Task mezcla resultados independientes;
- faltan verificaciones requeridas sin explicación;
- aparecen cambios fuera de alcance;
- se tomaron acciones no autorizadas;
- el reporte pretende aprobar su propio resultado o decidir la memoria posterior.

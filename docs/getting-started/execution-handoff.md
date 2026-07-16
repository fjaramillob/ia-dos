# Handoff entre Conversation Space y coding agent

Este flujo convierte una necesidad confirmada en planificación técnica o ejecución acotada, verificable y trazable.

Consulta primero:

- [Registro de tópicos conversacionales](../orchestration/topic-routing-registry.md);
- [Propiedad y retorno del ciclo](../orchestration/cycle-ownership.md);
- [Avance concreto y transición a coding agents](../orchestration/concrete-execution-flow.md);
- [Registro de tipos de ejecución](../execution/execution-task-types.md);
- [Autoridad de fuentes, artefactos y entornos](../execution/source-and-artifact-authority.md).

## Flujo

```text
Conversation Space
→ resultado esperado
→ Cycle Owner
→ Planning Task o Execution Task
→ coding agent
→ Implementation Plan o Execution Report
→ destino declarado
→ revisión e iteración
```

`00` no es una parada obligatoria.

## 1. Confirmar propiedad y destinos

Antes de delegar, registra:

- tópico y nombre del espacio;
- estado del resultado;
- Cycle Owner;
- destino del Implementation Plan;
- destino del Execution Report;
- espacio de escalamiento.

No uses un único campo `Retorno` cuando pueda confundirse el destino de distintos artefactos.

## 2. Aplicar el gate de planificación

Pregunta:

```text
¿El resultado está suficientemente definido,
es pequeño y puede ejecutarse con seguridad sin planificación técnica previa?
```

- **Sí:** prepara una Execution Task.
- **No por falta de inspección o diseño:** prepara una Planning Task.
- **No por una decisión de dominio pendiente:** continúa o deriva.
- **No por reorientación:** escala a `00`.

## 3. Preparar una Planning Task

Usa `templates/planning-task.template.md`.

Debe incluir:

- objetivo del plan;
- Cycle Owner y destinos;
- contexto mínimo;
- autoridad y acceso de fuentes, artefactos y entornos;
- inspección requerida;
- fuera de alcance;
- gate de tamaño;
- condiciones de detención;
- formato del Implementation Plan.

La Planning Task es solo lectura.

## 4. Revisar el Implementation Plan

Usa `templates/implementation-plan.template.md`.

El Cycle Owner compara:

- objetivo versus resultado propuesto;
- hechos versus inferencias;
- fuentes autorizadas versus fuentes utilizadas;
- dependencias y riesgos;
- unidades propuestas;
- decisiones humanas pendientes;
- primera tarea recomendada.

Aprueba solo una unidad ejecutable.

Plan producido no equivale a plan aprobado ni a ejecución autorizada.

## 5. Elegir el tipo de ejecución

Toda Execution Task declara un tipo principal:

```text
INSPECT | BOOTSTRAP | BUILD | FIX | REFACTOR | MIGRATE
TEST | HARDEN | DOCUMENT | WIKI | RELEASE | OPERATE
```

La planificación no es un tipo de materialización. Usa Planning Task cuando el objetivo sea diseñar cómo implementar.

No mezcles varios tipos para ocultar objetivos independientes.

## 6. Aplicar el gate de tamaño

Confirma:

```text
¿La tarea puede completarse, verificarse y reportarse
como una sola unidad sin mezclar resultados independientes?
```

Si no, divide antes de ejecutar.

## 7. Preparar la Execution Task

Usa `templates/execution-task.template.md`.

Debe incluir:

- Cycle Owner y destino del reporte;
- tipo de ejecución;
- objetivo único;
- contexto mínimo;
- autoridad y acceso de recursos;
- readiness del entorno;
- alcance y fuera de alcance;
- zonas autorizadas;
- criterios de aceptación;
- verificaciones;
- condiciones de detención;
- documentación o memoria;
- autorizaciones explícitas.

## 8. Preparar el entorno

Confirma únicamente:

- entorno disponible: local, remoto o combinado;
- recursos accesibles y faltantes;
- trabajo que debe preservarse;
- permisos reales;
- secretos o datos restringidos;
- acciones externas o con coste.

No impongas una estructura física o herramienta concreta.

## 9. Ejecutar con el coding agent

El agente debe:

1. confirmar objetivo, Cycle Owner y destino;
2. revisar instrucciones aplicables;
3. inspeccionar el estado real antes de escribir;
4. respetar autoridad, acceso y autorizaciones;
5. modificar solo el alcance aprobado;
6. detenerse ante contradicciones o riesgos;
7. ejecutar verificaciones aplicables;
8. revisar los cambios completos;
9. devolver el artefacto requerido al destino indicado.

## 10. Cerrar el ciclo

Después de aprobar el resultado:

- conserva implementación y evidencia en sus fuentes correspondientes;
- actualiza memoria solo con conocimiento confirmado;
- prepara una corrección o la siguiente unidad desde el mismo Cycle Owner;
- transfiere propiedad de forma explícita cuando cambie el dominio;
- escala a `00` solo por reorientación real.

## Rechaza el cierre cuando

- falta Cycle Owner o destino;
- una Planning Task produjo cambios;
- un plan se presenta como implementación;
- la Execution Task mezcla resultados independientes;
- faltan verificaciones exigidas sin explicación;
- aparecen cambios fuera de alcance;
- se tomaron acciones no autorizadas;
- memoria o documentación presenta propuestas como hechos.

## Verificación final

- [ ] El resultado y su estado están declarados.
- [ ] El Cycle Owner está definido.
- [ ] Los destinos de plan, reporte y escalamiento están separados.
- [ ] Se aplicó el gate de planificación.
- [ ] Se aplicó el gate de tamaño.
- [ ] La autoridad y acceso de recursos están explícitos.
- [ ] El entorno real fue confirmado sin imponer topología.
- [ ] Los criterios y verificaciones son observables.
- [ ] Las autorizaciones están declaradas.
- [ ] El artefacto vuelve al destino correcto.
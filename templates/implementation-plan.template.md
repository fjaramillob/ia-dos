# Implementation Plan

## Identificación

- Planning Task: `[PLAN-ID]`
- Proyecto: `[NOMBRE]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino de revisión: `[NORMALMENTE EL CYCLE OWNER]`
- Estado: `Propuesto | Requiere decisión | Bloqueado | Listo para revisión`
- Decisión técnica dominante: `[UNA SOLA DECISIÓN]`

## Fuentes y accesos utilizados

| Recurso | Rol | Autoridad para | Acceso utilizado | Limitaciones observadas |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `Lectura` | `[LÍMITES]` |

## Estado actual comprobado

Describe únicamente lo relevante para la decisión dominante:

- qué existe;
- qué no existe o no pudo verificarse;
- trabajo previo que debe preservarse;
- contradicciones aplicables;
- riesgos o restricciones activas.

Separa hechos, inferencias y propuestas.

## Decisión recomendada

Expresa la recomendación que el Cycle Owner debe aceptar, corregir o rechazar.

No la presentes como arquitectura aprobada ni implementación realizada.

## Estrategia mínima

Explica solo lo necesario para materializar la decisión:

- dependencias indispensables;
- artefactos o áreas afectadas;
- verificaciones necesarias;
- riesgos directos;
- condiciones de detención.

No conviertas el plan en un roadmap completo por defecto.

## Clasificación de decisiones pendientes

| Decisión | Clasificación | Tratamiento |
|---|---|---|
| `[DECISIÓN]` | `Bloqueante antes de ejecutar | Supuesto explícito | Alternativa del plan | Decisión posterior` | `[ACCIÓN]` |

Solo una decisión bloqueante antes de ejecutar impide preparar la primera Execution Task candidata. Las demás deben mantenerse visibles sin detener el avance.

## Primera unidad recomendada

- ID propuesto:
- tipo principal:
- resultado único:
- alcance:
- fuera de alcance:
- recursos necesarios:
- autorizaciones requeridas:
- criterios de aceptación:
- verificaciones mínimas:
- condiciones de detención:
- destino del Execution Report:

Incluye esta sección siempre que exista evidencia suficiente para definir una primera unidad segura.

## Execution Task candidata

Entrega un bloque autosuficiente listo para copiar al coding agent utilizando `execution-task.template.md` cuando la primera unidad pueda definirse con seguridad.

La tarea candidata:

- no autoriza ejecución hasta que el Cycle Owner la apruebe;
- debe contener un único resultado verificable;
- debe declarar supuestos, autorizaciones y condiciones de detención;
- no debe exigir al usuario reconstruirla desde el resto del plan.

Cuando no pueda prepararse, identifica una sola decisión bloqueante y explica por qué impide incluso definir una unidad segura.

## Unidades posteriores, solo si son necesarias

Enumera únicamente dependencias inmediatas que ayuden a entender la primera unidad. No diseñes toda la iniciativa salvo que ese sea el objetivo explícito de la Planning Task.

| Orden | Resultado único | Dependencia | Evidencia de cierre |
|---:|---|---|---|
| 2 | `[RESULTADO]` | `[DEPENDENCIA]` | `[EVIDENCIA]` |

## Brechas de otro dominio

- `[BRECHA Y TÓPICO AL QUE PERTENECE]`, o `Ninguna`.

No resuelvas silenciosamente decisiones funcionales, estratégicas, operativas o de cumplimiento desde un plan técnico.

Cuando la siguiente brecha pertenezca claramente a otro especialista y no requiera reorientación, recomienda un handoff directo a ese espacio, no un retorno intermedio a `00`.

No abras ese handoff antes de entregar la primera Execution Task candidata salvo que la brecha sea realmente bloqueante.

## Decisiones humanas pendientes

- `[DECISIÓN Y CLASIFICACIÓN]`, o `Ninguna`.

No propongas ejecutar mientras exista una decisión indispensable sin resolver. No trates como indispensable una decisión que pueda modelarse de forma segura mediante un supuesto reversible o una condición de detención.

## Memoria y documentación

Indica qué conocimiento deberá registrarse después de ser aceptado, implementado o verificado. Las propuestas no se registran como estado real.

## Declaración de solo lectura

- [ ] No se modificaron artefactos.
- [ ] No se realizaron cambios remotos ni despliegues.
- [ ] El plan no se trató como autorización de ejecución.
- [ ] Las limitaciones de acceso fueron declaradas.
- [ ] El alcance se mantuvo proporcional a la decisión dominante.
- [ ] Las decisiones pendientes fueron clasificadas como bloqueantes o no bloqueantes.
- [ ] Se incluyó una Execution Task candidata o una única razón bloqueante verificable.
- [ ] El plan vuelve al destino de revisión indicado.

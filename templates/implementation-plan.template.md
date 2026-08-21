# Implementation Plan

## Encabezado de retorno

```text
Artifact Type: Implementation Plan
Planning Task ID: [PLAN-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Sesión de planificación: [PLAN — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
```

## Identificación

- Planning Task: `[PLAN-ID]`
- Cycle ID: `[CYCLE-ID O NO APLICA]`
- Proyecto: `[NOMBRE]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Destino de revisión: `[NORMALMENTE EL CYCLE OWNER]`
- Sesión de planificación, cuando aporte: `[PLAN — RESULTADO | NO APLICA]`
- Rol ejecutado: `Coding Agent — Planning`
- Estado: `Listo para revisión | Bloqueado`
- Decisión técnica dominante: `[UNA SOLA DECISIÓN]`

## Fuentes y accesos utilizados

| Recurso | Rol | Autoridad para | Acceso utilizado | Limitaciones observadas |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `Lectura` | `[LÍMITES]` |

## Evidencia verificable

Cada hallazgo que condicione la decisión debe registrar:

| Recurso | Ruta o referencia | Estado observado | Interpretación | Límite |
|---|---|---|---|---|
| `[RECURSO]` | `[RUTA O ID]` | `[HECHO]` | `[SIGNIFICADO]` | `[LO QUE NO DEMUESTRA]` |

Una afirmación sin evidencia identificable se marca como inferencia o propuesta.

## Estado actual comprobado

Describe sólo lo relevante:

- qué existe;
- qué no existe o no pudo verificarse;
- trabajo previo que debe preservarse;
- contradicciones aplicables;
- riesgos o restricciones activas.

Separa hechos, inferencias y propuestas.

## Decisión recomendada

Expresa la recomendación que el Cycle Owner debe revisar.

No la presentes como arquitectura aprobada ni implementación realizada.

## Estrategia mínima

Explica sólo lo necesario para materializar la decisión:

- dependencias indispensables;
- artefactos o áreas afectadas;
- verificaciones necesarias;
- riesgos directos;
- condiciones de detención.

No conviertas el plan en un roadmap completo por defecto.

## Decisiones pendientes

| Decisión | Clasificación | Tratamiento |
|---|---|---|
| `[DECISIÓN]` | `Bloqueante antes de ejecutar | Supuesto explícito | Alternativa | Decisión posterior` | `[ACCIÓN]` |

Una decisión bloqueante impide preparar una unidad segura. Las demás permanecen visibles sin detener el avance.

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
- Execution Cell o sesión: `[NOMBRE O NO APLICA]`

Si el proyecto ya utiliza una Execution Cell adecuada y su conversación activa sigue respondiendo bien, reutilízala. No propongas una nueva sesión sólo porque el resultado tiene otro nombre.

## Execution Task candidata

Entrega un bloque autosuficiente listo para copiar cuando la primera unidad pueda definirse con seguridad.

La tarea candidata:

- no autoriza ejecución hasta recibir la aprobación aplicable;
- contiene un único resultado verificable;
- conserva el Cycle ID cuando exista;
- usa un Task ID distinto del Planning Task ID;
- declara `Execution Cell o sesión` sin forzar una conversación nueva;
- declara `Coding Agent — Execution` como rol activo;
- vuelve a declarar permisos, alcance y condiciones de detención;
- no exige reconstruirla desde el resto del plan.

La separación correcta es de **autoridad**, no necesariamente de conversación:

```text
Planning Task
→ Implementation Plan
→ revisión / aprobación aplicable
→ Execution Task
→ Execution Cell existente o sesión autorizada
→ Execution Report
```

La ejecución nunca hereda permisos del Planning, incluso cuando la herramienta reutiliza contexto.

Cuando no pueda prepararse una Execution Task candidata, identifica una sola razón bloqueante verificable.

## Unidades posteriores

Enumera únicamente dependencias inmediatas necesarias para comprender la primera unidad. No diseñes toda la iniciativa salvo objetivo explícito.

## Brechas de otro dominio

- `[BRECHA Y TÓPICO]`, o `Ninguna`.

No resuelvas silenciosamente decisiones funcionales, estratégicas, operativas o de cumplimiento desde un plan técnico.

Cuando la siguiente brecha pertenezca claramente a otro especialista y no requiera reorientación, recomienda un handoff directo.

## Decisiones humanas pendientes

- `[DECISIÓN Y CLASIFICACIÓN]`, o `Ninguna`.

No propongas ejecutar mientras exista una decisión humana indispensable sin resolver. No trates como indispensable una decisión que pueda mantenerse de forma segura mediante un supuesto reversible.

## Memoria y documentación

Indica únicamente documentación o conocimiento que la futura Execution Task deba actualizar explícitamente como parte de su alcance.

No agregues una sección de conocimiento potencialmente durable derivada automáticamente del plan. Las propuestas no se registran como estado real.

## Revisión requerida

El Cycle Owner revisa el plan dentro de su autoridad delegada y obtiene aprobación humana cuando corresponda.

El coding agent no selecciona por sí mismo la decisión de aprobar, corregir, rechazar o escalar.

## Declaración de solo lectura

- [ ] No se modificaron artefactos.
- [ ] No se realizaron cambios remotos ni despliegues.
- [ ] El plan no se trató como autorización de ejecución.
- [ ] Las limitaciones de acceso fueron declaradas.
- [ ] El alcance se mantuvo proporcional a la decisión dominante.
- [ ] Las decisiones pendientes fueron clasificadas.
- [ ] Se incluyó una Execution Task candidata o una razón bloqueante verificable.
- [ ] El plan vuelve al destino indicado.
- [ ] No se cambió el Cycle Owner ni se abrió otro ciclo.
- [ ] La futura ejecución mantiene autorización separada sin imponer una conversación nueva.

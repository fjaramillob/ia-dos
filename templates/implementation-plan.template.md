# Implementation Plan

## Encabezado de retorno

```text
Artifact Type: Implementation Plan
Planning Task ID: [PLAN-ID]
Cycle ID: [CYCLE-ID O NO APLICA]
Sesión de planificación: [PLAN — RESULTADO | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios al proyecto: Ninguno
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
- Materialización del propio plan: `[RUTA/NOMBRE AUTORIZADO | Conversación | NO APLICA]`

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

- Task ID: `PENDIENTE — lo asigna el Conversation Agent/Cycle Owner al adoptar la candidata`
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

El coding agent de Planning no asigna el Task ID de la futura Execution Task. Puede identificar la unidad con un título descriptivo dentro del plan, pero la identidad operativa se asigna únicamente cuando el Conversation Agent/Cycle Owner adopta y construye la Execution Task real.

Si el proyecto ya utiliza una Execution Cell adecuada y su conversación activa sigue respondiendo bien, reutilízala. No propongas una nueva sesión sólo porque el resultado tiene otro nombre.

## Execution Task candidata

Entrega un bloque autosuficiente listo para revisión cuando la primera unidad pueda definirse con seguridad.

La candidata puede estar estructuralmente lista para copiar, pero **no es todavía una Execution Task autorizada** y mantiene el `Task ID` pendiente.

La tarea candidata:

- no autoriza ejecución hasta recibir la aprobación aplicable;
- contiene un único resultado verificable;
- conserva el Cycle ID cuando exista;
- declara `Task ID: PENDIENTE — ASIGNAR AL ADOPTAR`;
- no inventa ni reserva un Task ID por cuenta del coding agent;
- declara `Execution Cell o sesión` sin forzar una conversación nueva;
- declara `Coding Agent — Execution` como rol futuro;
- vuelve a declarar permisos, alcance y condiciones de detención;
- no exige reconstruirla desde el resto del plan.

Cuando el Cycle Owner adopta la candidata, el Conversation Agent:

1. revisa la evidencia y el alcance propuesto;
2. resuelve la autorización humana aplicable;
3. asigna el Task ID;
4. valida o completa el contrato de Execution Task;
5. sólo entonces la entrega a `Coding Agent — Execution`.

La separación correcta es de **autoridad**, no necesariamente de conversación:

```text
Planning Task
→ Implementation Plan
→ revisión / aprobación aplicable
→ Conversation Agent asigna Task ID y construye Execution Task
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

El coding agent no selecciona por sí mismo la decisión de aprobar, corregir, rechazar o escalar y no asigna el Task ID de la candidata.

## Declaración de solo lectura

- [ ] No se modificaron artefactos, datos, configuración ni estado del proyecto inspeccionado.
- [ ] Si Output Delivery lo autorizó, sólo se materializó este Implementation Plan en el destino declarado.
- [ ] No se realizaron cambios remotos ni despliegues.
- [ ] El plan no se trató como autorización de ejecución.
- [ ] Las limitaciones de acceso fueron declaradas.
- [ ] El alcance se mantuvo proporcional a la decisión dominante.
- [ ] Las decisiones pendientes fueron clasificadas.
- [ ] Se incluyó una Execution Task candidata o una razón bloqueante verificable.
- [ ] El Task ID de la candidata quedó pendiente para el Conversation Agent/Cycle Owner.
- [ ] El plan vuelve al destino indicado.
- [ ] No se cambió el Cycle Owner ni se abrió otro ciclo.
- [ ] La futura ejecución mantiene autorización separada sin imponer una conversación nueva.

La materialización autorizada del propio Implementation Plan no convierte Planning en una operación de escritura sobre el producto.

# Project Start Planning Brief

Usa este perfil cuando el producto sea nuevo o el repositorio esté vacío o casi vacío y sea necesario definir una fundación técnica mínima antes de ejecutar.

No reemplaza la Planning Task. La especializa para inicios de proyecto.

## Identificación

- Cycle ID: `[CYCLE-BOOTSTRAP-N O NO APLICA]`
- Planning Task ID: `[PLAN-BOOTSTRAP-N]`
- Proyecto: `[NOMBRE]`
- Preparada por: `[CONVERSATION SPACE]`
- Ejecutada por: `[CODING AGENT]`
- Cycle Owner: `[CONVERSATION SPACE]`
- Sesión de planificación, cuando aporte: `PLAN — BOOTSTRAP | NO APLICA`
- Rol activo: `Coding Agent — Planning`
- Estado: `Propuesta | Aprobada | En análisis | Bloqueada | Completada`

Incluye `templates/agent-role-contract.template.md` cuando aporte.

## Misión

Describe en una frase qué fundación técnica debe quedar recomendada y qué primera capacidad verificable debe habilitar.

Ejemplo conceptual:

```text
Determinar la fundación técnica mínima que permita levantar el proyecto de forma reproducible y ejecutar una primera capacidad verificable sin diseñar todavía toda la arquitectura.
```

## Decisión única

Formula una sola pregunta que el Implementation Plan debe responder.

```text
¿Cuál es la fundación técnica mínima y la primera unidad segura que deben implementarse para iniciar este producto?
```

## Estado inicial confirmado

Incluye únicamente hechos relevantes:

- estado real del repositorio objetivo;
- decisiones vigentes;
- memoria durable disponible cuando exista;
- sistema heredado o referencias, cuando existan;
- trabajo que debe preservarse;
- restricciones no negociables;
- elementos que no deben copiarse ni asumirse.

## Orden de inspección

1. Leer instrucciones locales aplicables.
2. Leer estado actual y decisiones vigentes necesarias.
3. Inspeccionar el repositorio objetivo.
4. Consultar referencias heredadas sólo para dudas concretas.
5. Verificar herramientas, versiones y checks existentes.

No obligues al coding agent a leer toda la documentación de IA-DOS o toda la LLM Wiki.

## Fuentes, autoridad y acceso

| Recurso | Rol | Autoridad para | Acceso | Límite |
|---|---|---|---|---|
| `[PRODUCTO]` | implementación objetivo | estado técnico real | lectura | sin cambios |
| `[MEMORIA]` | decisiones y contexto | estado aceptado | lectura | contrastar con implementación |
| `[HEREDADO]` | evidencia histórica | patrones y aprendizaje | lectura | no copiar automáticamente |
| `IA-DOS` | método | roles, tareas y retorno | referencia | no decide el stack |

## Baseline técnico a evaluar

Evalúa sólo lo aplicable:

- runtime y versiones;
- gestor de dependencias;
- estructura mínima;
- variables de entorno;
- tratamiento de secretos;
- comandos de desarrollo;
- lint y formato;
- typecheck;
- pruebas mínimas;
- build reproducible;
- manejo inicial de errores y logs;
- instrucciones locales para futuros agentes;
- documentación mínima para levantar el proyecto;
- CI mínima sólo cuando esté autorizada y aporte.

No impongas tecnología sin evidencia.

## Primera capacidad verificable

El plan no debe terminar sólo en una estructura que compile.

Propón una capacidad observable que demuestre el fundamento elegido manteniendo un único resultado ejecutable.

Declara:

- comportamiento observable;
- invariantes;
- prueba positiva;
- prueba negativa cuando corresponda;
- evidencia esperada en el Execution Report.

## Fuera de alcance

Lista únicamente exclusiones necesarias para mantener pequeño el primer ciclo.

No incluyas un inventario completo del roadmap futuro.

## Entregable requerido

El Implementation Plan debe contener:

1. encabezado de retorno IA-DOS;
2. evidencia inspeccionada;
3. decisión recomendada;
4. baseline técnico propuesto;
5. estructura mínima;
6. primera capacidad verificable;
7. riesgos, supuestos y decisiones indispensables;
8. una sola Execution Task candidata tipo `BOOTSTRAP` u otro tipo justificado;
9. estado `LISTO PARA REVISIÓN` o `BLOQUEADO`.

La Execution Task candidata debe declarar:

- `Task ID: PENDIENTE — ASIGNAR AL ADOPTAR`;
- `Execution Cell o sesión: [NOMBRE O NO APLICA]`;
- rol futuro `Coding Agent — Execution`;
- permisos de escritura requeridos;
- criterios y pruebas;
- destino del Execution Report;
- estado `Candidata pendiente de aprobación`.

El Coding Agent — Planning no asigna ni reserva el Task ID. El Conversation Agent/Cycle Owner lo asigna únicamente al revisar y adoptar la candidata como Execution Task real.

No declares que se abrirá una sesión de ejecución nueva por defecto. Si el proyecto ya tiene una Execution Cell adecuada y activa, la futura tarea puede reutilizarla. La autorización de ejecución sigue siendo separada del Planning y se vuelve a declarar completa.

## Readiness

Si la candidata depende de runtime, servicio, acceso, secreto o conectividad indispensable no comprobados, el plan debe señalar un `Environment Preflight` antes de autorizar escritura.

## Restricciones

- no implementar;
- no crear ni modificar archivos;
- no instalar dependencias;
- no crear ramas, commits o PR;
- no asignar el Task ID de la futura Execution Task;
- no diseñar el roadmap completo;
- no detallar unidades posteriores independientes;
- no copiar arquitectura heredada;
- no clonar IA-DOS sin autorización;
- no responder como Conversation Space o Project Orchestrator.

## Cierre

```text
Artifact Type: Implementation Plan
Planning Task ID: [PLAN-BOOTSTRAP-N]
Cycle ID: [CYCLE-ID O NO APLICA]
Sesión de planificación: [PLAN — BOOTSTRAP | NO APLICA]
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
```

El coding agent no aprueba la candidata ni asigna su Task ID. El Cycle Owner revisa dentro de la autoridad delegada y la persona responsable conserva la aprobación final cuando corresponda.

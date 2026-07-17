# Project Start Planning Brief

Usa este perfil cuando el producto sea nuevo o el repositorio esté vacío o casi vacío y sea necesario definir una fundación técnica mínima antes de ejecutar.

No reemplaza la Planning Task. La especializa para inicios de proyecto.

## Identificación

- Cycle ID: `[CYCLE-BOOTSTRAP-N]`
- Planning Task ID: `[PLAN-BOOTSTRAP-N]`
- Proyecto: `[NOMBRE]`
- Preparada por: `[CONVERSATION SPACE ESPECIALISTA]`
- Ejecutada por: `[CODING AGENT]`
- Revisada por: `[CYCLE OWNER]`
- Agent Session: `PLAN — BOOTSTRAP`
- Rol activo: `Coding Agent — Planning`
- Estado: `Propuesta | Aprobada | En análisis | Bloqueada | Completada`

Incluye `templates/agent-role-contract.template.md` como contrato embebido.

## Misión

Describe en una frase qué fundación técnica debe quedar decidida y qué primera capacidad verificable debe habilitar.

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
- memoria durable disponible;
- sistema heredado o referencias, cuando existan;
- trabajo que debe preservarse;
- restricciones no negociables;
- elementos que no deben copiarse ni asumirse.

## Orden de inspección

1. Leer instrucciones locales aplicables, como `AGENTS.md` o equivalentes.
2. Leer estado actual y decisiones vigentes.
3. Inspeccionar el repositorio objetivo.
4. Consultar referencias heredadas únicamente para resolver dudas concretas.
5. Verificar herramientas, versiones y checks existentes.

No obligues al coding agent a leer toda la documentación de IA-DOS. La tarea debe contener el contrato metodológico necesario.

## Fuentes, autoridad y acceso

| Recurso | Rol | Autoridad para | Acceso | Límite |
|---|---|---|---|---|
| `[PRODUCTO]` | implementación objetivo | estado técnico real | lectura | sin cambios |
| `[MEMORIA]` | decisiones y contexto | estado aceptado | lectura | contrastar con implementación |
| `[HEREDADO]` | evidencia histórica | patrones y aprendizajes | lectura | no copiar automáticamente |
| `IA-DOS` | método | roles, tareas y retorno | referencia | no decide el stack |

## Baseline técnico a evaluar

Evalúa solo lo aplicable al proyecto:

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
- CI mínima, solo cuando esté autorizada y aporte.

No impongas una tecnología concreta sin evidencia.

## Primera capacidad verificable

El plan no debe terminar solo en una estructura que compile.

Debe proponer una capacidad observable que demuestre el fundamento elegido, manteniendo un único resultado ejecutable.

Declara:

- comportamiento observable;
- invariantes;
- prueba positiva;
- prueba negativa, cuando corresponda;
- evidencia que deberá regresar en el Execution Report.

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
8. una sola Execution Task candidata tipo `BOOTSTRAP` u otro tipo mejor justificado;
9. estado `LISTO PARA REVISIÓN` o `BLOQUEADO`.

La Execution Task candidata debe declarar:

- Task ID: `[EXEC-BOOTSTRAP-N]`;
- Agent Session: `BOOTSTRAP`;
- Rol activo: `Coding Agent — Execution`;
- que se abrirá una sesión independiente de la sesión de planificación;
- permisos de escritura exactos;
- criterios y pruebas;
- destino del Execution Report;
- estado `Candidata pendiente de aprobación`.

## Restricciones

- no implementar;
- no crear ni modificar archivos;
- no instalar dependencias;
- no crear ramas, commits o PR;
- no diseñar el roadmap completo;
- no detallar unidades posteriores;
- no copiar la arquitectura heredada;
- no clonar IA-DOS sin autorización;
- no responder como Conversation Space o Project Orchestrator.

## Cierre obligatorio

```text
Artifact: Implementation Plan
Planning Task ID: [PLAN-BOOTSTRAP-N]
Agent Session: PLAN — BOOTSTRAP
Cycle Owner: [CONVERSATION SPACE]
Estado: LISTO PARA REVISIÓN | BLOQUEADO
Cambios realizados: Ninguno
Decisión requerida: Aprobar | Corregir | Rechazar | Escalar
```
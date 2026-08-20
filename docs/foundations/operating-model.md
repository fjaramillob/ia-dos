# Modelo operativo

IA-DOS organiza el desarrollo asistido por inteligencia artificial mediante ciclos pequeños de dirección, razonamiento, materialización y verificación.

Su secuencia maestra es:

```text
Dirigir
→ entender
→ decidir
→ delimitar
→ materializar
→ verificar y aprender
```

`Dirigir` expresa la responsabilidad transversal de la persona y del Project Orchestrator. Los cinco movimientos siguientes se repiten según las necesidades del proyecto y no constituyen fases rígidas.

## 1. Dirigir

La persona responsable define propósito, prioridades, restricciones y autoridad. El Project Orchestrator mantiene la visión transversal y convierte esa dirección en trabajo coordinado.

Esta capa debe:

- capturar propósito y dirección suficientes;
- separar conversaciones por dominio cuando desbloquea trabajo;
- identificar prioridades, decisiones e hipótesis;
- seleccionar las fuentes y el contexto necesarios;
- preservar memoria durable antes de depender de historia conversacional;
- transformar necesidades en unidades de trabajo acotadas;
- revisar resultados y señalar qué conocimiento debe conservarse.

Dirigir no significa ejecutar cada modificación. Significa decidir qué debe ocurrir, por qué y bajo qué límites.

## 2. Entender

Antes de actuar se revisa evidencia suficiente sobre el estado real.

Esto puede incluir:

- propósito y usuario;
- comportamiento existente;
- estructura del repositorio;
- arquitectura vigente cuando exista;
- decisiones confirmadas;
- riesgos y restricciones;
- pruebas disponibles;
- cambios locales pendientes;
- límites de acceso, coste o seguridad.

El objetivo no es completar una auditoría exhaustiva. Es reducir los supuestos que podrían afectar la siguiente decisión.

Cuando una fuente no está disponible, el Orchestrator o el coding agent debe declararlo y evitar inventar información.

## 3. Decidir

Se confirma una decisión pequeña, reversible y útil para avanzar.

Debe distinguirse explícitamente entre:

- hecho verificado;
- preferencia;
- supuesto;
- propuesta;
- decisión de trabajo;
- decisión durable;
- pregunta abierta.

Una conversación puede explorar alternativas, pero una propuesta no se transforma en decisión ni en implementación sin la autoridad correspondiente.

Las decisiones que deban reutilizarse regresan a la memoria durable, ADR, registro de decisiones u otra fuente canónica aplicable.

## 4. Delimitar

Antes de solicitar planificación o modificación física se define una unidad de trabajo acotada.

Si la unidad depende de conocimiento relevante que sólo vive en conversaciones, primero se aplica el [Memory Bootstrap Gate](memory-bootstrap-gate.md).

Una `Execution Task` debe indicar:

- objetivo;
- contexto durable estrictamente necesario;
- referencias y lectura requerida cuando corresponda;
- alcance y fuera de alcance;
- autoridad de fuentes y recursos;
- zonas autorizadas;
- permisos y acciones externas;
- criterios de aceptación;
- verificaciones esperadas;
- condiciones de detención;
- destino del reporte.

El Project Orchestrator prepara o coordina esta delimitación. La tarea debe ser suficientemente clara para que otra herramienta pueda ejecutarla sin depender del historial completo del chat.

## 5. Materializar

El coding agent modifica los artefactos reales dentro de los límites declarados.

Puede trabajar sobre:

- implementación;
- documentación;
- memoria durable;
- configuración;
- pruebas;
- branches, commits y pull requests cuando estén autorizados.

Durante esta etapa debe:

- inspeccionar antes de modificar;
- confirmar recurso y branch o modo de trabajo cuando corresponda;
- leer sólo el contexto requerido;
- evitar cambios no solicitados;
- no introducir dependencias o refactors sin justificación y autorización;
- detenerse si falta una decisión importante;
- ejecutar verificaciones aplicables;
- revisar el diff;
- devolver un `Execution Report` con evidencia.

El coding agent no debe recibir automáticamente todo IA-DOS, toda la memoria durable o todos los proyectos del workspace.

## 6. Verificar y aprender

El resultado se compara con la `Execution Task`, no con la confianza que inspire la respuesta del agente.

La verificación puede incluir:

- revisión del diff;
- lint;
- typecheck;
- build;
- pruebas unitarias o de integración;
- revisión visual;
- revisión de seguridad;
- pasos manuales reproducibles;
- capturas, logs o evidencia relevante.

Después de aprobar el cambio se actualiza la fuente de verdad correspondiente:

- implementación en el artefacto técnico real;
- evidencia en el `Execution Report`, diff, pull request u otro mecanismo;
- decisión o estado durable en la memoria o ADR cuando deba reutilizarse;
- trabajo pendiente en el sistema elegido;
- documentación cuando cambió el comportamiento.

Aprender significa conservar únicamente conocimiento confirmado y útil, no copiar conversaciones completas a la memoria durable.

## Arquitectura de trabajo

```text
Persona responsable
        ↓
Project Orchestrator
        ↓
Conversation Spaces ligeros
        ↓
Decisión o necesidad clara
        ↓
Memory Bootstrap Gate, cuando aplica
        ↓
Planning Task | Environment Preflight | Execution Task
        ↓
Coding agent
        ↓
Implementation Plan | cambios + verificaciones + Execution Report
        ↓
Cycle Owner revisa
        ↓
Fuentes de verdad actualizadas cuando corresponde
```

## Frontera de responsabilidad

```text
Project Orchestrator
    define qué debe cambiar y por qué

Coding agent
    realiza el cambio físico y entrega evidencia
```

El Orchestrator no debe presentar una propuesta como si ya estuviera implementada. El coding agent no debe ampliar silenciosamente la decisión, el alcance o la autoridad recibida.

## Flujo de contexto

```text
IA-DOS
    ↓ contrato operativo
Project Orchestrator
    ↓ contexto durable necesario + referencias/lecturas + delta + tarea
coding agent
    ↓ plan o cambios + verificaciones + reporte
Cycle Owner y persona responsable
    ↓ revisión y decisión
fuentes de verdad correspondientes
```

Los `Context Packs` pueden seguir utilizándose como patrón opcional cuando un proyecto obtiene valor de agrupar rutas o documentos, pero no forman parte del contrato mínimo ni del Wiki Starter vigente.

## Fuentes de verdad

IA-DOS busca evitar que la misma información se mantenga manualmente en varios lugares.

| Tipo de información | Destino recomendado |
|---|---|
| Propósito y estado reusable | memoria durable del proyecto |
| Arquitectura vigente | registro arquitectónico o memoria durable cuando exista |
| Decisión durable | registro de decisiones adoptado por el proyecto |
| Instrucciones del Orchestrator | configuración o artefacto de orquestación adoptado |
| Instrucciones para coding agents | `AGENTS.md` o política equivalente |
| Trabajo pendiente | sistema de seguimiento elegido por el proyecto |
| Alcance de un plan | `Planning Task` |
| Propuesta de implementación | `Implementation Plan` |
| Alcance de una ejecución | `Execution Task` |
| Implementación | artefactos reales del producto |
| Revisión y evidencia | `Execution Report`, diff, pull request o mecanismo equivalente |
| Historial TASK/REPORT | Exchange cuando el proyecto lo adopta |
| Estándar común reutilizable | repositorio IA-DOS |

La tarea puede enlazar estos artefactos, pero no debe duplicarlos sin necesidad.

Consulta [Método de trabajo](working-method.md) para la explicación conceptual de los cinco movimientos.
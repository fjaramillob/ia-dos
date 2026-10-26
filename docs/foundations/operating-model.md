# Modelo operativo

IA-DOS organiza el desarrollo asistido por IA mediante ciclos pequeños de dirección, razonamiento, materialización y verificación.

Su secuencia maestra es:

```text
Dirigir
→ entender
→ decidir
→ delimitar
→ materializar
→ verificar y aprender
```

`Dirigir` expresa la responsabilidad transversal de la persona y del Project Orchestrator. Los movimientos siguientes se repiten según las necesidades del proyecto y no constituyen fases rígidas.

## 1. Dirigir

La persona responsable define propósito, prioridades, restricciones y autoridad. El Project Orchestrator mantiene visión transversal y convierte esa dirección en trabajo coordinado.

Esta capa debe:

- capturar propósito y dirección suficientes;
- abrir Conversation Spaces sólo cuando separar un dominio desbloquea trabajo;
- identificar prioridades, decisiones e hipótesis;
- seleccionar fuentes y contexto necesarios;
- aplicar Memory Bootstrap Gate antes de depender de historia conversacional;
- definir Protected Invariants, Adaptation Authority y Protected Boundaries;
- identificar readiness que deba conocerse antes de autorizar una frontera sensible;
- transformar necesidades en outcomes acotados y verificables;
- revisar resultados y evaluar después qué conocimiento merece persistirse.

Dirigir no significa ejecutar cada modificación.

## 2. Entender

Antes de actuar se revisa evidencia suficiente sobre el estado real.

Puede incluir:

- propósito y usuario;
- comportamiento existente;
- estructura del repositorio;
- arquitectura vigente;
- decisiones confirmadas;
- riesgos y restricciones;
- pruebas disponibles;
- cambios locales pendientes;
- límites de acceso, coste o seguridad;
- readiness del entorno cuando sea indispensable.

El objetivo no es una auditoría exhaustiva, sino reducir los supuestos que podrían afectar la siguiente decisión.

Cuando una fuente no está disponible, decláralo y evita inventar información.

## 3. Decidir

Se confirma una decisión pequeña, reversible y útil para avanzar.

Distingue:

- hecho verificado;
- preferencia;
- supuesto;
- propuesta;
- decisión de trabajo;
- decisión durable;
- pregunta abierta.

Una propuesta no se transforma en decisión ni implementación sin autoridad suficiente.

El Cycle Owner actúa dentro de la autoridad delegada. La persona responsable conserva la aprobación final cuando la decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

## 4. Delimitar

Antes de solicitar planificación o modificación física se define una unidad acotada.

Si depende de conocimiento relevante que sólo vive en conversaciones, aplica primero [Memory Bootstrap Gate](memory-bootstrap-gate.md).

Si el readiness de una precondición debe conocerse antes de conceder autoridad sensible, usa `Environment Preflight`. De otro modo, la Execution Task revalida internamente las condiciones volátiles.

Cuando existe una decisión material de diseño todavía no resuelta, usa `Planning Task` en solo lectura. El detalle de implementación se planifica internamente durante Execution.

Una `Execution Task` debe indicar proporcionalmente:

- outcome;
- Protected Invariants;
- Adaptation Authority;
- Protected Boundaries;
- contexto durable estrictamente necesario;
- referencias y lectura requerida cuando corresponda;
- alcance y fuera de alcance;
- autoridad de fuentes y recursos;
- Execution Cell o sesión cuando aplique;
- zonas autorizadas;
- permisos y acciones externas;
- criterios de aceptación;
- verificaciones esperadas;
- condiciones de detención;
- destino del reporte.

La tarea debe poder ejecutarse sin depender del historial completo del chat.

## 5. Materializar

El coding agent modifica los artefactos reales dentro de los límites declarados.

Puede trabajar sobre implementación, documentación, configuración, pruebas o memoria durable **sólo cuando la tarea lo autoriza**.

Durante esta etapa debe:

- inspeccionar y revalidar antes de modificar;
- confirmar outcome, Protected Invariants, Protected Boundaries y Adaptation Authority;
- planificar internamente el cómo;
- leer sólo el contexto requerido;
- preservar fuera de alcance;
- ante un fallo reversible dentro de `BOUNDED`, diagnosticar, reparar y safe-retry dentro de la misma Task;
- detenerse si cambiar el método exige alterar un invariante o cruzar una frontera nueva;
- ejecutar verificaciones aplicables;
- revisar el diff;
- devolver un `Execution Report` con evidencia.

El coding agent no debe recibir automáticamente todo IA-DOS, toda la LLM Wiki o todos los proyectos del workspace.

## 6. Verificar y aprender

El resultado se compara con la `Execution Task`, no con la confianza que inspire la respuesta del agente.

La verificación puede incluir diff, lint, typecheck, build, pruebas, revisión visual, seguridad, pasos manuales reproducibles, capturas, logs u otra evidencia relevante.

El `Execution Report` utiliza:

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

El reporte es evidencia. No aprueba el cambio ni elige la siguiente acción de gobierno. Puede actualizar memoria `LOCAL` autorizada; cuando el impacto es estructural y el proyecto adopta `90`, reporta `ROUTE_TO_90` para custodia separada.

Después de revisar la evidencia:

- la implementación permanece en el artefacto técnico real;
- la evidencia permanece en Report, diff, PR u otro mecanismo;
- el trabajo pendiente permanece en el sistema elegido;
- la memoria durable se actualiza únicamente con conocimiento confirmado que deba reutilizarse y mediante una acción autorizada.

Aprender significa conservar conocimiento útil y confirmado, no copiar conversaciones completas o REPORT enteros a la memoria.

## Arquitectura de trabajo

```text
Persona responsable
        ↓
Project Orchestrator
        ↓
Conversation Space / Cycle Owner
        ↓
resultado claro
        ↓
Memory Bootstrap Gate, cuando aplica
        ↓
Planning Task, sólo si existe decisión material no resuelta
        ↓
Environment Preflight, sólo si readiness debe conocerse antes de una frontera sensible
        ↓
Execution Task outcome-first + Revalidate
        ↓
Execution Cell o entorno autorizado
        ↓
Coding Agent
        ↓
Execution Report
        ↓
Cycle Owner revisa dentro de autoridad delegada
        ↓
Persona responsable aprueba cuando corresponde
        ↓
Fuentes de verdad actualizadas cuando corresponde
```

## Frontera de responsabilidad

```text
Persona responsable
    define dirección y conserva aprobación final aplicable

Project Orchestrator / Cycle Owner
    gobierna y delimita dentro de autoridad delegada

Coding Agent — Planning
    inspecciona y propone

Coding Agent — Execution
    decide el cómo dentro de Protected Invariants/Adaptation Authority
    realiza el cambio autorizado y entrega evidencia
```

El Orchestrator no presenta una propuesta como implementada. El coding agent no amplía silenciosamente objetivo, alcance o autoridad.

## Flujo de contexto

```text
IA-DOS
    ↓ contrato operativo
Project Orchestrator
    ↓ contexto durable necesario + referencias/lecturas + delta + tarea
coding agent
    ↓ plan o cambios + verificaciones + evidencia
Cycle Owner y persona responsable
    ↓ revisión y decisión según autoridad
fuentes de verdad correspondientes
```

`Context Pack` es un término histórico/compatible, no parte del contrato mínimo vigente. La selección actual de contexto se expresa mediante contexto durable necesario, referencias y lectura requerida.

## Fuentes de verdad

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
| Readiness del entorno | `Environment Readiness Report` |
| Alcance de una ejecución | `Execution Task` |
| Implementación | artefactos reales del producto |
| Evidencia | `Execution Report`, diff, PR o mecanismo equivalente |
| Historial de archivos intercambiados | Exchange cuando el proyecto lo adopta |
| Estándar común reutilizable | repositorio IA-DOS |

La tarea puede enlazar estos artefactos, pero no debe duplicarlos sin necesidad.

Consulta [Método de trabajo](working-method.md).

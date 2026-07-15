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

- capturar el alma y la dirección del proyecto;
- separar conversaciones por dominio cuando desbloquea trabajo;
- identificar prioridades, decisiones e hipótesis;
- seleccionar las fuentes y el contexto necesarios;
- transformar necesidades en unidades de trabajo acotadas;
- revisar resultados y señalar qué conocimiento debe conservarse.

Dirigir no significa ejecutar cada modificación. Significa decidir qué debe ocurrir, por qué y bajo qué límites.

## 2. Entender

Antes de actuar se revisa evidencia suficiente sobre el estado real.

Esto puede incluir:

- propósito y usuario;
- comportamiento existente;
- estructura del repositorio;
- arquitectura vigente;
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

Las decisiones durables regresan a la wiki, ADR, issue u otra fuente canónica aplicable.

## 4. Delimitar

Antes de solicitar una modificación física se define una unidad de trabajo acotada.

La `Execution Task` debe indicar:

- objetivo;
- problema o evidencia inicial;
- contexto mínimo y rutas que deben leerse;
- alcance;
- fuera de alcance;
- archivos o repositorios autorizados;
- guardrails;
- criterios de aceptación;
- pruebas esperadas;
- condiciones de detención;
- documentación o memoria que puede requerir actualización;
- formato del reporte final.

El Project Orchestrator prepara o coordina esta delimitación. La tarea debe ser suficientemente clara para que otra herramienta pueda ejecutarla sin depender del historial completo del chat.

## 5. Materializar

El coding agent modifica los artefactos reales dentro de los límites declarados.

Puede trabajar sobre:

- implementación;
- documentación;
- LLM Wiki;
- configuración;
- pruebas;
- branches, commits y pull requests.

Durante esta etapa debe:

- inspeccionar antes de modificar;
- confirmar repositorio y branch;
- leer solo el contexto necesario;
- evitar cambios no solicitados;
- no introducir dependencias o refactors sin justificación;
- detenerse si falta una decisión importante;
- ejecutar verificaciones aplicables;
- revisar el diff;
- devolver un `Execution Report` con evidencia.

El coding agent no debe recibir automáticamente todo IA-DOS, toda la wiki o todos los proyectos del workspace.

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

- implementación en el repositorio de aplicación;
- evidencia en el pull request o `Execution Report`;
- decisión o estado durable en la wiki o ADR;
- trabajo pendiente en el issue o mecanismo elegido;
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
Decisiones e hipótesis confirmadas
        ↓
Execution Task
        ↓
Coding agent
        ↓
Repositorio de aplicación / LLM Wiki
        ↓
Branch + cambios + pruebas
        ↓
Pull request + Execution Report
        ↓
Revisión humana y del Orchestrator
        ↓
Merge
        ↓
Actualización de memoria durable
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
    ↓ Context Pack + Execution Task
Coding agent
    ↓ cambios + pruebas + Execution Report
Project Orchestrator y persona responsable
    ↓ revisión y decisión
Wiki / issue / ADR / PR
```

## Fuentes de verdad

IA-DOS busca evitar que la misma información se mantenga manualmente en varios lugares.

| Tipo de información | Destino recomendado |
|---|---|
| Propósito y estado del proyecto | Wiki |
| Arquitectura vigente | Wiki |
| Decisión durable | Registro de decisión en la wiki o ADR |
| Instrucciones del Orchestrator | Configuración del Project, Gem o archivo de orquestación |
| Instrucciones para coding agents | `AGENTS.md` |
| Trabajo pendiente | GitHub Issue o mecanismo elegido por el proyecto |
| Alcance del cambio | `Execution Task` |
| Implementación | Repositorio de aplicación |
| Revisión y evidencia | Pull request o `Execution Report` |
| Estándar común reutilizable | Repositorio IA-DOS |

La tarea puede enlazar estos artefactos, pero no debe duplicarlos sin necesidad.

Consulta [Método de trabajo](working-method.md) para la explicación conceptual de los cinco movimientos.
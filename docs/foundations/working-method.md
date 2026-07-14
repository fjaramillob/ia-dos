# El método IA-DOS

IA-DOS hace explícita, reproducible y transferible una forma de dirigir proyectos de software con inteligencia artificial.

No busca reemplazar el criterio de quien dirige el proyecto. Busca convertir ese criterio en un método que pueda compartirse entre personas, asistentes conversacionales, coding agents, repositorios y memoria durable sin crear fuentes de verdad paralelas.

## Principio fundamental

> Pensar, decidir, materializar y verificar son responsabilidades distintas.

IA-DOS separa esas responsabilidades para evitar que un chat actúe como repositorio, que un coding agent invente estrategia o que una decisión quede atrapada en una conversación.

## El ciclo de trabajo

```text
Entender
→ decidir
→ delimitar
→ materializar
→ verificar
→ registrar y aprender
```

### Entender

Leer la evidencia disponible y capturar la dirección suficiente para avanzar. Entender no significa auditar todo ni agotar todas las preguntas.

### Decidir

Confirmar una decisión pequeña, útil, reversible cuando sea posible y coherente con la dirección del proyecto. Una propuesta del asistente no es una decisión hasta que la persona responsable la confirma.

### Delimitar

Convertir la decisión en una unidad de trabajo acotada con objetivo, contexto mínimo, alcance, fuera de alcance, criterios de aceptación, pruebas y condiciones de detención.

### Materializar

Entregar la unidad de trabajo a un coding agent con acceso controlado al repositorio o workspace. El coding agent inspecciona, modifica archivos, ejecuta pruebas y prepara evidencia.

### Verificar

Revisar el diff, las pruebas y el reporte contra la tarea original. La afirmación de un agente no es evidencia suficiente.

### Registrar y aprender

Actualizar la fuente de verdad correspondiente: código, issue, pull request, ADR, estado o LLM Wiki. El aprendizaje durable debe quedar fuera de los chats.

## Actores y responsabilidades

### Persona responsable

- define propósito y prioridades;
- confirma decisiones importantes;
- autoriza cambios sensibles;
- revisa evidencia;
- decide cuándo aceptar o detener el trabajo.

### Project Orchestrator

- mantiene la dirección transversal;
- organiza Conversation Spaces cuando reducen complejidad;
- distingue hechos, hipótesis, propuestas y decisiones;
- transforma decisiones en trabajo delimitado;
- selecciona contexto mínimo;
- prepara prompts y handoffs;
- revisa resultados y decide qué conocimiento debe registrarse.

El Project Orchestrator coordina. No debe asumir que aprobar una estrategia autoriza modificar repositorios.

### Conversation Spaces

Los Conversation Spaces razonan sobre dominios concretos como producto, arquitectura, ejecución o memoria.

- no existen por simetría;
- cada uno debe tener una responsabilidad diferenciada;
- deben trabajar con una misión concreta y un entregable que desbloquee el siguiente paso;
- producen decisiones, recomendaciones, handoffs o tareas;
- no son memoria durable.

Cuando un Conversation Space no dispone de capacidades de repositorio, no debe simular ramas, commits, pull requests ni modificaciones de archivos.

### Coding agents

Los coding agents materializan trabajo autorizado.

- inspeccionan antes de modificar;
- trabajan dentro del alcance declarado;
- modifican código o documentación;
- ejecutan validaciones aplicables;
- preparan commits o pull requests cuando corresponde;
- devuelven un Execution Report con evidencia.

### LLM Wiki

La LLM Wiki conserva memoria durable de alta señal: propósito, estado real, arquitectura vigente, decisiones, riesgos, fuentes y contexto transversal.

La wiki describe el proyecto; no sustituye el código, los issues ni los pull requests. Se instala temprano con una estructura mínima y se puebla progresivamente con conocimiento confirmado.

## Pensar no es construir

```text
Project Orchestrator y Conversation Spaces
→ entienden, recomiendan, deciden y delimitan

Coding agents
→ inspeccionan, modifican, prueban y reportan
```

Una misma herramienta puede ofrecer ambas capacidades, pero IA-DOS mantiene la separación lógica. Antes de actuar se debe comprobar qué acceso real tiene la herramienta y qué acción fue autorizada.

## Flujo de colaboración

```text
Persona responsable
→ Project Orchestrator
→ Conversation Space
→ decisión confirmada
→ Execution Task
→ coding agent
→ repositorio o LLM Wiki
→ pruebas + Execution Report + pull request
→ revisión
→ merge
→ aprendizaje durable
```

## Criterio de simplicidad

IA-DOS no agrega chats, documentos, agentes o procesos porque existan en la plantilla. Cada elemento debe justificar su existencia porque reduce ambigüedad, protege el proyecto o desbloquea trabajo.

## Resultado esperado

Un proyecto que adopta IA-DOS debe poder cambiar de asistente o coding agent sin perder dirección, memoria ni control. La forma de trabajar permanece estable aunque cambien las herramientas.
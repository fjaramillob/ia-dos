# El método IA-DOS

IA-DOS es un método abierto para dirigir proyectos de software junto a inteligencia artificial.

Su propósito no es reemplazar la forma de trabajar de una persona. Busca hacerla explícita, reproducible y transferible entre asistentes conversacionales, coding agents, repositorios y herramientas distintas.

## Principio fundamental

> La dirección y el criterio viven en la orquestación. La materialización vive en los coding agents.

IA-DOS separa deliberadamente cuatro responsabilidades:

```text
Dirigir y decidir
→ razonar por dominios
→ materializar cambios
→ verificar y conservar aprendizaje
```

La separación evita que un chat se transforme en fuente de verdad, que un coding agent improvise estrategia o que una modificación se considere terminada sin evidencia.

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

Leer las fuentes disponibles y comprender lo suficiente para avanzar. No significa auditar todo ni resolver el proyecto completo antes de comenzar.

### Decidir

Confirmar una decisión pequeña, útil, reversible y coherente con la dirección del proyecto. Lo no resuelto permanece como hipótesis, propuesta o pregunta abierta.

### Delimitar

Convertir la decisión en una `Execution Task` con objetivo, contexto mínimo, alcance, fuera de alcance, rutas autorizadas, criterios, pruebas y condiciones de detención.

### Materializar

Delegar la modificación física a un coding agent con acceso controlado al repositorio o workspace. El agente inspecciona, modifica, prueba y reporta.

### Verificar

Comparar el resultado con la tarea mediante diff, pruebas y evidencia observable. La afirmación de un agente no constituye evidencia suficiente.

### Registrar y aprender

Actualizar la fuente de verdad correspondiente: código, wiki, ADR, issue, pull request, estado o Context Pack. La memoria crece con conocimiento confirmado, no con transcripciones completas.

## Actores y responsabilidades

```text
Persona responsable
        ↓
Project Orchestrator
        ↓
Conversation Spaces
        ↓
Execution Task
        ↓
Coding agent
        ↓
Repositorio + pruebas + Execution Report
        ↓
Revisión y decisión humana
        ↓
Memoria durable
```

### Persona responsable

Define propósito y prioridades, confirma decisiones relevantes, autoriza accesos y cambios, revisa evidencia y conserva la responsabilidad final.

### Project Orchestrator

Mantiene la visión transversal, propone estrategia, organiza conversaciones, convierte decisiones en trabajo acotado, selecciona contexto y revisa resultados.

El Project Orchestrator no debe asumir que una aprobación conceptual autoriza modificaciones. Tampoco debe actuar como sustituto permanente del coding agent.

### Conversation Spaces

Razonan sobre un dominio específico y producen decisiones, recomendaciones, flujos o handoffs. No existen por obligación: cada espacio debe reducir mezcla de contexto o desbloquear un resultado concreto.

Por defecto, los Conversation Spaces no mantienen Git ni materializan cambios en repositorios. Cuando una plataforma tenga capacidades de escritura, la autorización, el alcance y la evidencia siguen siendo obligatorios.

### Coding agents

Inspeccionan y modifican archivos dentro de límites declarados. Pueden trabajar sobre el repositorio de aplicación, la LLM Wiki o documentación cuando la tarea lo autoriza.

### LLM Wiki

Conserva propósito, estado, arquitectura, decisiones, riesgos, fuentes y contexto durable. Su estructura puede instalarse temprano, pero se puebla progresivamente con evidencia y aprendizaje reales.

### GitHub y Git

Issues y `Execution Tasks` delimitan trabajo. Branches, commits y pull requests trazan modificaciones. Pruebas, revisiones y reportes sostienen la verificación.

## Pensar no es construir

Una conversación puede producir una recomendación excelente sin haber modificado ningún archivo. Un coding agent puede producir código correcto sin tener autoridad para redefinir el producto.

IA-DOS mantiene ambas capacidades conectadas, pero no las confunde:

```text
Conversación
→ entiende, propone y delimita

Coding agent
→ inspecciona, materializa y prueba
```

## Autorización

Distingue siempre:

```text
decisión aprobada
→ propuesta de cambio
→ autorización explícita
→ ejecución
→ validación
→ evidencia
```

La ceremonia debe escalar con el riesgo. Un ajuste documental pequeño y reversible no requiere el mismo control que una migración, eliminación, cambio de datos, producción o infraestructura.

## Contexto mínimo

Cada herramienta recibe solo lo necesario:

```text
CORE
+ Context Pack relevante
+ Execution Task
```

No se entrega automáticamente todo IA-DOS, toda la wiki o todos los repositorios.

## Resultado esperado

IA-DOS permite que distintas herramientas colaboren sobre un mismo proyecto sin perder dirección, control ni aprendizaje:

- la persona dirige;
- el Orchestrator organiza;
- los Conversation Spaces razonan;
- las tareas delimitan;
- los coding agents materializan;
- Git traza;
- la evidencia verifica;
- la LLM Wiki recuerda.

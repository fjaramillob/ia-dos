# Responsabilidades humanas y de la IA

IA-DOS parte de una regla simple:

> La IA puede proponer, organizar y ejecutar dentro de límites. La responsabilidad final sigue siendo humana.

## Persona responsable

La persona que dirige el proyecto debe:

- definir propósito, prioridades y restricciones;
- confirmar decisiones importantes;
- autorizar accesos y cambios sensibles;
- decidir qué herramientas pueden leer o modificar cada fuente;
- revisar evidencia y aceptar o rechazar resultados;
- decidir cuándo una tarea está terminada;
- proteger secretos, datos y recursos;
- pedir ayuda especializada cuando el riesgo lo exige.

La supervisión humana no requiere realizar manualmente cada cambio. Requiere conservar autoridad sobre dirección, riesgo y aprobación.

## Project Orchestrator

El asistente conversacional que coordina el proyecto debe:

- comprender la estructura IA-DOS adoptada;
- consultar la wiki, repositorios y fuentes canónicas disponibles;
- capturar y mantener la dirección transversal;
- separar Conversation Spaces cuando exista mezcla de contexto o una especialización desbloquee trabajo;
- distinguir hechos, preferencias, supuestos, propuestas, decisiones y preguntas abiertas;
- ayudar a confirmar decisiones pequeñas, reversibles y útiles;
- transformar necesidades en `Execution Tasks`;
- seleccionar el contexto mínimo necesario;
- definir qué debe cambiar, por qué y bajo qué límites;
- preparar handoffs claros para coding agents;
- revisar el `Execution Report`, el diff y la evidencia disponible;
- señalar qué conocimiento confirmado debe regresar a la memoria durable;
- evitar que una conversación se convierta en una fuente de verdad paralela.

El Project Orchestrator piensa, organiza y delega. No debe afirmar que modificó un repositorio, ejecutó pruebas o creó un pull request cuando no dispone de la capacidad y evidencia para hacerlo.

## Conversation Spaces

Los espacios especializados razonan sobre un dominio concreto, por ejemplo producto, arquitectura, ejecución o memoria.

Deben:

- trabajar con una misión y un entregable explícitos;
- recibir un handoff autosuficiente y ligero;
- mantener separado lo confirmado de lo exploratorio;
- producir decisiones, recomendaciones, tareas o síntesis utilizables;
- devolver un handoff de salida cuando otro espacio depende de su resultado.

No son fases obligatorias ni fuentes de verdad durables.

## Coding agent

El agente que trabaja sobre archivos, repositorios o entornos debe:

- leer las instrucciones y fuentes autorizadas;
- confirmar repositorio, branch y alcance antes de modificar;
- distinguir hechos de supuestos;
- inspeccionar antes de actuar;
- leer solamente el contexto necesario;
- crear o modificar los artefactos autorizados;
- preservar el comportamiento fuera de alcance;
- evitar dependencias, refactors o cambios adicionales no solicitados;
- detenerse cuando falta acceso, existe una contradicción o se requiere una decisión;
- ejecutar las verificaciones aplicables;
- revisar el diff completo;
- reportar archivos, cambios, pruebas, errores, riesgos y pendientes;
- devolver un `Execution Report` compatible con la tarea.

La materialización puede afectar código, documentación o LLM Wiki. Que una tarea sea documental no elimina la necesidad de autorización, alcance, diff y evidencia.

## Frontera entre organización y materialización

```text
Project Orchestrator
    comprende, decide, delimita y revisa

Coding agent
    inspecciona, materializa, prueba y reporta
```

El Orchestrator define qué debe cambiar y por qué. El coding agent realiza el cambio físico.

Ninguna de estas funciones reemplaza la aprobación humana cuando existe impacto relevante en seguridad, costes, producción, datos, arquitectura o alcance.

## Límites comunes

Ningún asistente o agente debe:

- ampliar alcance silenciosamente;
- convertir una propuesta en decisión aprobada;
- presentar como implementado algo sin evidencia;
- modificar producción como primera opción;
- crear costes sin autorización;
- exponer secretos o datos sensibles;
- debilitar seguridad para completar una tarea;
- ocultar errores o pruebas fallidas;
- inventar decisiones históricas;
- tratar su propia conversación o sesión como memoria durable;
- asumir acceso a repositorios o archivos que no fueron entregados;
- fusionar cambios sin la autorización correspondiente.

Consulta [Método de trabajo](working-method.md) y [Coding agents](../execution/coding-agents.md).
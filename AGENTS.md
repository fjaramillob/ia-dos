# AGENTS.md

## Propósito del repositorio

Este repositorio contiene IA-DOS, un framework abierto para organizar proyectos de software desarrollados con asistencia de inteligencia artificial.

IA-DOS coordina tanto la capa conversacional de dirección como la ejecución realizada por coding agents.

## Archivos de entrada

Antes de modificar el repositorio:

1. Lee `README.md` y `docs/index.md`.
2. Si la tarea afecta asistentes externos, lee `ORCHESTRATOR.md` y `docs/foundations/orchestration-layer.md`.
3. Identifica el alcance exacto de la tarea.

## Reglas para agentes

1. No agregues conceptos, herramientas, carpetas o procesos que no estén solicitados.
2. No presentes como implementado algo que solo está propuesto.
3. Mantén el contenido principal en español.
4. Conserva en inglés los nombres técnicos ampliamente establecidos cuando corresponda, por ejemplo `README.md`, `AGENTS.md`, `issue`, `pull request`, `branch`, `commit`, `Context Pack`, `Conversation Space`, `Project Orchestrator` y `Execution Task`.
5. Explica cada término técnico la primera vez que aparezca.
6. Evita lenguaje promocional, promesas futuras y complejidad no validada.
7. Mantén IA-DOS independiente de una herramienta específica.
8. No incluyas referencias a proyectos particulares en el estándar común.
9. Distingue la capa de orquestación conversacional de la capa de ejecución técnica.
10. No trates las conversaciones como fuente de verdad durable.

## Alcance actual

La etapa actual es fundacional. El repositorio debe definir de forma simple:

- propósito y alcance;
- público objetivo;
- principios;
- capa de orquestación conversacional;
- modelo operativo;
- estructura recomendada del workspace;
- adopción por proyectos;
- relación entre LLM Wiki, app, Conversation Spaces y coding agents;
- gobierno y contribución.

Quedan fuera de alcance por ahora:

- aplicaciones;
- agentes propios;
- CLI;
- scripts automáticos;
- integraciones ejecutables;
- dashboards;
- evaluadores de madurez;
- automatizaciones complejas.

## Criterios de calidad

Todo cambio debe:

- resolver una necesidad clara;
- ser comprensible para una persona que no sea programadora experta;
- evitar duplicar información existente;
- mantener enlaces y términos consistentes;
- distinguir hechos, recomendaciones, opciones y excepciones;
- incluir una explicación práctica cuando introduzca una regla nueva;
- demostrar cómo la conversación se convierte en un artefacto durable o un input de desarrollo cuando corresponda;
- considerar el consumo de contexto y tokens.

## Verificación mínima

Antes de cerrar una tarea:

- revisa el diff completo;
- verifica que los enlaces relativos sean correctos;
- confirma que no existan contradicciones entre documentos;
- confirma que el alcance declarado coincida con los archivos modificados;
- reporta cualquier supuesto o decisión pendiente.
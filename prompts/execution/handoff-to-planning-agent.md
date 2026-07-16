# Prompt de handoff hacia planificación técnica

Utiliza este prompt después de aprobar una `Planning Task`.

```text
Actúa como coding agent en modo de planificación técnica para una única Planning Task.

Antes de comenzar:
1. Lee la Planning Task canónica completa.
2. Consulta solo las fuentes, artefactos y entornos autorizados.
3. Confirma Cycle Owner, destino del Implementation Plan y espacio de escalamiento.
4. Confirma que el modo es solo lectura.
5. Declara cualquier limitación de acceso antes de inferir el estado.

Durante la planificación:
- inspecciona el estado real;
- distingue hechos, inferencias y propuestas;
- respeta la autoridad de cada recurso;
- no modifiques artefactos;
- no crees commits, cambios remotos, despliegues o recursos externos;
- no amplíes el objetivo;
- divide la iniciativa en unidades pequeñas, dependientes y verificables;
- detente cuando se active una condición de detención.

Al finalizar, entrega un `Implementation Plan` que incluya:
- fuentes y accesos utilizados;
- estado actual comprobado;
- limitaciones y contradicciones;
- resultado final propuesto;
- estrategia de implementación;
- división en Execution Tasks;
- primera tarea recomendada;
- decisiones humanas pendientes;
- memoria o documentación futura;
- declaración de solo lectura.

Devuelve el plan al destino indicado.
No ejecutes la primera tarea ni prepares cambios físicos sin una Execution Task posterior.
```
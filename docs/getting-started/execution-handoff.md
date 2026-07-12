# Handoff entre Project Orchestrator y coding agent

Este flujo convierte una necesidad de desarrollo en una tarea acotada, verificable y trazable.

## Flujo completo

```text
Necesidad o decisión
→ Execution Task
→ revisión humana
→ handoff al coding agent
→ implementación y pruebas
→ Execution Report
→ revisión de evidencia
→ actualización de wiki, issue o ADR
```

## 1. Crear la Execution Task

Usa `templates/execution-task.template.md`.

La tarea debe definir una única fuente canónica y contener:

- objetivo;
- contexto mínimo;
- problema o evidencia;
- alcance y fuera de alcance;
- repositorios y rutas autorizadas;
- guardrails;
- criterios de aceptación observables;
- pruebas esperadas;
- condiciones de detención;
- documentación y memoria que deben actualizarse;
- formato de entrega.

No delegues una tarea que todavía depende de una decisión importante sin resolver.

## 2. Revisar antes de delegar

El Project Orchestrator y la persona responsable deben confirmar:

- que el objetivo es terminable;
- que el alcance es suficientemente pequeño;
- que las rutas autorizadas son correctas;
- que el fuera de alcance protege comportamiento no relacionado;
- que las pruebas son aplicables;
- que el agente tiene acceso solo al contexto necesario;
- que las condiciones de detención son claras.

## 3. Construir el handoff

El handoff debe incluir:

```text
CORE
+ Context Pack principal
+ Context Pack secundario, solo si es necesario
+ Execution Task canónica
+ AGENTS.md del repositorio
```

Evita adjuntar toda la wiki, toda la historia de conversaciones o todos los repositorios del workspace.

## 4. Ejecución del coding agent

El agente debe:

1. leer `AGENTS.md`;
2. revisar el estado Git;
3. validar alcance y rutas;
4. inspeccionar antes de modificar;
5. ejecutar solo cambios autorizados;
6. detenerse ante una condición definida;
7. ejecutar pruebas aplicables;
8. revisar el diff completo;
9. devolver un `Execution Report`.

## 5. Reporte de ejecución

Usa `templates/execution-report.template.md`.

El reporte debe distinguir:

- trabajo completado;
- trabajo parcial;
- bloqueos;
- pruebas ejecutadas;
- pruebas no ejecutadas;
- desviaciones;
- riesgos;
- decisiones pendientes;
- actualizaciones recomendadas para la wiki.

Una afirmación del agente no sustituye evidencia.

## 6. Revisión del retorno

El Project Orchestrator compara el reporte con la tarea original.

Debe comprobar:

- cada criterio de aceptación;
- evidencia de pruebas;
- diff y archivos modificados;
- respeto del fuera de alcance;
- desviaciones aprobadas o no aprobadas;
- riesgos y limitaciones;
- información durable que cambió.

El estado `Completada` solo corresponde cuando los criterios aplicables tienen evidencia suficiente.

## 7. Cierre y memoria

Al cerrar:

- la implementación queda en el repositorio de aplicación;
- el estado de la tarea se actualiza en su fuente canónica;
- la evidencia queda en el pull request o reporte;
- las decisiones durables vuelven a la wiki o ADR;
- `current-state.md` se actualiza cuando cambió el estado real;
- `CORE` solo se actualiza si cambió información transversal.

## Condiciones de rechazo del reporte

No cierres la tarea cuando:

- faltan pruebas exigidas sin explicación;
- los criterios de aceptación no tienen evidencia;
- aparecen cambios fuera de alcance;
- el agente ocultó fallos o trabajo incompleto;
- el working tree o diff no coincide con el reporte;
- se tomaron decisiones no autorizadas;
- la documentación presenta propuestas como implementadas.

## Resultado esperado

Este flujo permite que el trabajo pase de conversación a implementación y vuelva a memoria durable sin depender de la confianza ciega en el agente.
# Prompt de handoff hacia un coding agent

Utiliza este prompt después de aprobar una `Execution Task`.

```text
Actúa como coding agent para una única tarea acotada.

Antes de modificar:
1. Lee `AGENTS.md` del repositorio.
2. Lee la `Execution Task` canónica completa.
3. Consulta solo el `CORE`, Context Packs y rutas indicadas en la tarea.
4. Ejecuta `git status` y reporta cambios previos no identificados.
5. Confirma objetivo, alcance, fuera de alcance, rutas autorizadas, pruebas y condiciones de detención.

Durante la ejecución:
- inspecciona antes de escribir;
- modifica solo lo autorizado;
- no amplíes alcance ni tomes decisiones de producto o arquitectura no aprobadas;
- no modifiques producción, secretos, recursos externos o dependencias salvo autorización explícita;
- detente cuando se active una condición de detención;
- ejecuta las pruebas aplicables;
- revisa el diff completo.

Al finalizar, entrega un `Execution Report` que incluya:
- estado: completada, parcial o bloqueada;
- resumen del resultado;
- archivos modificados;
- pruebas ejecutadas, resultados y evidencia;
- criterios de aceptación comprobados;
- fuera de alcance respetado;
- desviaciones;
- riesgos y limitaciones;
- decisiones pendientes;
- actualizaciones recomendadas para la wiki.

No afirmes que la tarea está completa sin evidencia suficiente.
```

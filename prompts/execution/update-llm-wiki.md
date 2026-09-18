# Prompt para ejecutar una Wiki Update Task

Utiliza este prompt sólo cuando la memoria sea el resultado principal de una Execution Task separada: bootstrap, consolidación de varios outcomes, reparación, migración documental o una frontera de autoridad distinta.

No lo uses como paso rutinario después de cada ejecución si la Task original ya podía actualizar memoria dentro del mismo outcome.

La tarea pegada debe ser una `Execution Task` canónica o el perfil `Wiki Update Task` vigente.

```text
Actúa como Coding Agent — Execution y materializa únicamente la actualización documental autorizada.

Antes de modificar:
1. valida `Artifact Type`, `Destination Role`, `Task ID`, `Cycle ID` cuando exista y Cycle Owner;
2. valida la precondición `Memory Bootstrap Gate` declarada por la tarea;
3. confirma que el motivo de separación sea bootstrap, consolidación, reparación, migración o frontera de autoridad distinta;
4. si declara `BOOTSTRAP REQUIRED — ESTA TAREA MATERIALIZA EL CHECKPOINT`, confirma que el único resultado sea persistir ese checkpoint y que la unidad original esté fuera de alcance;
5. confirma el recurso de memoria, branch o modo de trabajo y rutas autorizadas;
6. lee `AGENTS.md` de la LLM Wiki cuando exista;
7. lee `.ia-dos.yaml` sólo cuando exista y la tarea o el proyecto lo requieran;
8. identifica el home real cuando ya exista, o confirma que el alcance autoriza crearlo durante un bootstrap;
9. lee únicamente las páginas indicadas como `Lectura requerida`;
10. inspecciona el estado real de la memoria y las fuentes autorizadas;
11. detente si una contradicción relevante cambia el contenido que debería registrarse.

Durante la ejecución:
- modifica únicamente las rutas autorizadas;
- preserva contenido vigente fuera de alcance;
- no inventes información;
- no conviertas propuestas en hechos;
- no presentes como implementado algo sin evidencia técnica;
- distingue `Implementado`, `Decidido / aprobado pero no implementado`, `Pendiente`, `Fuera de alcance` y `Desconocido`;
- usa Markdown estándar y enlaces relativos como referencias canónicas;
- no dependas de wikilinks, plugins de Obsidian o formatos propietarios para semántica crítica;
- si consolidas varios outcomes, sintetiza el estado resultante en lugar de copiar cronología operacional;
- si actualizas un Operational Baseline, distingue HEAD remoto verificado de commit/versión productiva y conserva deployment/release, entorno y fecha cuando apliquen;
- no crees `log.md`, `tasks/`, `context-packs/` o páginas vacías salvo alcance explícito;
- no guardes secretos ni datos no permitidos;
- si esta tarea es un memory bootstrap, no continúes con la unidad original que busca desbloquear.

Validación:
- revisa Markdown y enlaces relativos afectados;
- valida YAML sólo cuando exista;
- verifica navegación desde el home real cuando haya sido afectada;
- revisa el diff completo;
- confirma que no existen cambios fuera de las rutas autorizadas;
- si es bootstrap, confirma que el checkpoint puede revisarse como memoria durable sin depender del chat para el conocimiento que debía persistir;
- reporta cualquier lectura o validación que no haya podido ejecutarse.

Entrega:
- devuelve un `Execution Report` canónico al Cycle Owner;
- usa `Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO`;
- usa `Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]`;
- registra `Durable Memory Impact: UPDATED` o la desviación real;
- registra `Operational Baseline: UPDATED | UNCHANGED | NO APLICA | BLOQUEADO`;
- enumera archivos creados, modificados o eliminados;
- indica fuentes consultadas;
- registra autorizaciones utilizadas, validaciones y evidencia;
- reporta desviaciones, contradicciones y pendientes del alcance original;
- realiza branch, commit, push o pull request sólo si cada acción está autorizada;
- no apruebes tu propio resultado ni fusiones sin autorización explícita;
- no propongas por defecto conocimiento durable adicional fuera del alcance autorizado;
- no elijas la decisión de gobierno posterior ni inicies otra unidad.

Si durante la ejecución aparece un hecho adicional que no debe incorporarse bajo esta tarea, consérvalo como evidencia normal del resultado y usa `Atención requerida` únicamente cuando necesite una decisión concreta.

Si la tarea materializó un checkpoint requerido por Memory Bootstrap, el reporte no habilita automáticamente la unidad original: el Cycle Owner debe revisarlo y reevaluar ese gate.

Wiki Update Task:
[PEGAR AQUÍ LA TAREA COMPLETA]
```

# Prompt para ejecutar una Wiki Update Task

Utiliza este prompt para entregar a un coding agent una actualización autorizada de memoria durable Markdown.

La tarea pegada debe ser una `Execution Task` canónica o el perfil `Wiki Update Task` vigente.

```text
Actúa como Coding Agent — Execution y materializa únicamente la actualización documental autorizada.

Antes de modificar:
1. valida `Artifact Type`, `Destination Role`, `Task ID`, `Cycle ID` cuando exista y Cycle Owner;
2. valida la precondición `Memory Bootstrap Gate` declarada por la tarea;
3. si declara `BOOTSTRAP REQUIRED — ESTA TAREA MATERIALIZA EL CHECKPOINT`, confirma que el único resultado sea persistir ese checkpoint y que la unidad original esté fuera de alcance;
4. confirma el recurso de memoria, branch o modo de trabajo y rutas autorizadas;
5. lee `AGENTS.md` de la LLM Wiki cuando exista;
6. lee `.ia-dos.yaml` sólo cuando exista y la tarea o el proyecto lo requieran;
7. identifica el home real cuando ya exista, o confirma que el alcance autoriza crearlo durante un bootstrap;
8. lee únicamente las páginas indicadas como `Lectura requerida`;
9. inspecciona el estado real de la memoria y las fuentes autorizadas;
10. detente si una contradicción relevante cambia el contenido que debería registrarse.

Durante la ejecución:
- modifica únicamente las rutas autorizadas;
- preserva contenido vigente fuera de alcance;
- no inventes información;
- no conviertas propuestas en hechos;
- no presentes como implementado algo sin evidencia técnica;
- distingue `Implementado`, `Decidido / aprobado pero no implementado`, `Pendiente`, `Fuera de alcance` y `Desconocido`;
- usa Markdown estándar y enlaces relativos como referencias canónicas;
- no dependas de wikilinks, plugins de Obsidian o formatos propietarios para semántica crítica;
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

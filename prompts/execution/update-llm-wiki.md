# Prompt para ejecutar una Wiki Update Task

Utiliza este prompt para entregar a un coding agent una actualización autorizada de memoria durable Markdown.

La tarea pegada debe ser una `Execution Task` canónica o el perfil `Wiki Update Task` vigente.

```text
Actúa como Coding Agent — Execution y materializa únicamente la actualización documental autorizada.

Antes de modificar:
1. valida `Artifact Type`, `Destination Role`, `Task ID`, `Cycle ID` cuando exista y Cycle Owner;
2. confirma el recurso de memoria, branch o modo de trabajo y rutas autorizadas;
3. lee `AGENTS.md` de la memoria;
4. lee `.ia-dos.yaml` sólo cuando exista y la tarea o el proyecto lo requieran;
5. identifica el home real: `00-home.md` en el starter vigente o la ruta equivalente declarada por una Wiki existente;
6. lee únicamente las páginas indicadas como `Lectura requerida`;
7. inspecciona el estado real de la memoria y las fuentes autorizadas;
8. detente si una contradicción relevante cambia el contenido que debería registrarse.

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
- no guardes secretos ni datos no permitidos.

Validación:
- revisa Markdown y enlaces relativos afectados;
- valida YAML sólo cuando exista;
- verifica navegación desde el home real cuando haya sido afectada;
- revisa el diff completo;
- confirma que no existen cambios fuera de las rutas autorizadas;
- reporta cualquier lectura o validación que no haya podido ejecutarse.

Entrega:
- devuelve un `Execution Report` canónico al Cycle Owner;
- enumera archivos creados, modificados o eliminados;
- indica fuentes consultadas;
- registra autorizaciones utilizadas, validaciones y evidencia;
- reporta desviaciones, contradicciones, riesgos y pendientes;
- señala conocimiento potencialmente durable adicional sin incorporarlo automáticamente;
- realiza branch, commit, push o pull request sólo si cada acción está autorizada;
- no apruebes tu propio resultado ni fusiones sin autorización explícita.

Wiki Update Task:
[PEGAR AQUÍ LA TAREA COMPLETA]
```

# Prompt para ejecutar una Wiki Update Task

Utiliza este prompt para entregar a Codex, Antigravity, Claude Code u otro coding agent una actualización autorizada de la LLM Wiki.

```text
Actúa como coding agent responsable de materializar una Wiki Update Task.

Antes de modificar:
1. confirma el repositorio, branch y rutas autorizadas;
2. lee AGENTS.md, .ia-dos.yaml, index.md y solo las páginas indicadas;
3. inspecciona el estado real de la wiki;
4. compara la tarea con las fuentes entregadas;
5. detente si existe una contradicción que requiera una decisión.

Durante la ejecución:
- modifica únicamente las rutas autorizadas;
- preserva contenido vigente fuera de alcance;
- no inventes información;
- no conviertas hipótesis o propuestas en hechos;
- no presentes como implementado algo sin evidencia;
- mantiene enlaces, navegación y formatos coherentes;
- actualiza log.md solo cuando las reglas de la wiki lo exijan;
- no guardes secretos ni datos no permitidos.

Validación:
- revisa Markdown, YAML, enlaces y navegación según corresponda;
- confirma la distinción entre implementado, planificado y desconocido;
- revisa el diff completo;
- confirma que no existen cambios fuera de las rutas autorizadas.

Entrega:
- devuelve un Execution Report;
- enumera archivos creados, modificados o eliminados;
- indica fuentes utilizadas;
- registra validaciones y resultados;
- reporta contradicciones, riesgos y pendientes;
- prepara branch, commits y pull request solo si la tarea lo autoriza;
- no fusiones sin autorización explícita.

Wiki Update Task:
[PEGAR AQUÍ LA TAREA COMPLETA]
```

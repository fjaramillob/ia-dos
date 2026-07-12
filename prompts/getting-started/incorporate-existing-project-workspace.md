# Prompt para incorporar un proyecto existente al workspace

Este prompt está dirigido a Codex, Claude Code, Antigravity u otro agente con acceso al sistema de archivos y Git.

```text
Objetivo
Incorporar formalmente un proyecto existente al workspace IA-DOS sin alterar su historia, mover archivos a ciegas ni modificar código.

Primera fase
Trabaja en modo lectura.

Antes de actuar
1. Detecta el sistema operativo.
2. Identifica la ruta absoluta del proyecto existente.
3. Detecta repositorios Git anidados o relacionados.
4. Reporta remotes, rama principal y `git status`.
5. Identifica documentación, wiki, scripts, pipelines, despliegues y archivos de configuración relevantes.
6. Señala si existen cambios locales no identificados.
7. No asumas que debes mover o renombrar el proyecto.

Clasificación requerida
Determina cuál escenario aplica:
A. app y wiki ya separadas;
B. app sin wiki;
C. app y documentación en el mismo repositorio;
D. proyecto fuera del workspace recomendado;
E. monorepo;
F. estructura ambigua o múltiples repositorios sin relación confirmada.

Acciones permitidas en modo lectura
- listar carpetas relevantes;
- leer configuración no sensible;
- ejecutar comandos Git de solo lectura;
- identificar rutas y dependencias estructurales;
- preparar una propuesta de adopción;
- registrar riesgos y contradicciones.

Acciones prohibidas sin autorización adicional
- mover o renombrar carpetas;
- ejecutar `git init` en un repositorio existente;
- cambiar remotes;
- cambiar rama principal;
- crear commits;
- borrar o reemplazar documentación;
- copiar secretos;
- crear repositorios remotos;
- modificar código, pipelines o despliegues.

Propuesta de adopción
Entrega una propuesta con:
- ruta actual de la app;
- ruta recomendada de la app;
- ruta propuesta o existente de la wiki;
- modelo: app/wiki separadas, monorepo o excepción documentada;
- riesgos de mover o no mover;
- impacto sobre rutas, scripts, pipelines y colaboradores;
- pasos reversibles;
- decisiones que requieren aprobación.

Segunda fase
Solo después de aprobación explícita, ejecuta las acciones autorizadas para:
- clonar el repositorio en una carpeta vacía;
- crear una wiki hermana;
- crear un `index.md` mínimo;
- inicializar Git en una wiki nueva;
- registrar rutas y excepciones.

Condiciones de detención
Detente cuando:
- `git status` muestre cambios no identificados;
- los remotes no coincidan con lo esperado;
- existan repositorios anidados no comprendidos;
- mover el proyecto pueda romper rutas, pipelines o despliegues;
- no esté clara la ubicación de secretos;
- la documentación contradiga la implementación;
- falte autorización para cualquier escritura;
- no pueda determinarse la fuente de verdad de la implementación.

Validaciones obligatorias
- historia Git preservada;
- remotes sin cambios;
- ningún archivo movido sin autorización;
- rutas absolutas registradas;
- app y wiki identificadas;
- excepción documentada cuando no se usa la estructura recomendada;
- ausencia de secretos en los reportes;
- siguiente paso definido.

Reporte final
Entrega:
1. sistema operativo;
2. estructura detectada;
3. repositorios y rutas;
4. estado Git;
5. documentación o wiki existente;
6. clasificación del escenario;
7. propuesta adoptada;
8. acciones ejecutadas;
9. acciones omitidas;
10. riesgos y decisiones pendientes;
11. siguiente paso recomendado.

No inicies cambios funcionales ni refactorizaciones durante esta tarea.
```

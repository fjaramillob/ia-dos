# Prompt para instalar IA-DOS

Este prompt está pensado para Codex, Claude Code, Antigravity u otro agente con acceso al sistema de archivos y Git.

## Prompt

```text
Objetivo
Instalar IA-DOS una sola vez como referencia local dentro del workspace autorizado, sin sobrescribir carpetas ni crear, mover o modificar recursos de proyectos existentes.

Contexto
Repositorio oficial:
https://github.com/fjaramillob/ia-dos.git

Nombre recomendado de la carpeta local:
00-ia-dos

Resultado físico esperado:
<workspace>/
└── 00-ia-dos/

Esta instalación no define la topología de ningún proyecto adoptante.

Antes de actuar
1. Detecta el sistema operativo.
2. Identifica la ruta exacta del workspace indicada por el usuario.
3. Muestra la ruta absoluta que utilizarás.
4. Verifica si ya existe una carpeta llamada 00-ia-dos.
5. Verifica si Git está instalado.
6. Confirma que instalar IA-DOS no requiere mover, renombrar o reorganizar proyectos existentes.

Acciones permitidas
- crear la carpeta raíz del workspace cuando no exista y esté autorizada;
- clonar IA-DOS como 00-ia-dos;
- ejecutar comandos Git de solo lectura para verificar la instalación;
- reportar rutas, remote, rama y estado del repositorio.

Acciones prohibidas
- crear app, Wiki, Exchange u otros recursos de proyecto como parte de esta instalación;
- imponer una estructura app/wiki;
- sobrescribir una carpeta existente;
- borrar, mover o renombrar proyectos existentes;
- modificar main;
- crear commits;
- modificar archivos dentro de IA-DOS;
- abrir todo el workspace a otros agentes;
- copiar IA-DOS dentro de cada proyecto;
- guardar secretos o credenciales.

Condiciones de detención
Detente sin realizar cambios cuando:
- 00-ia-dos ya existe;
- la ruta es ambigua;
- Git no está disponible;
- el clone requiere resolver un problema de autenticación;
- el remote obtenido no coincide con el repositorio oficial;
- detectas riesgo de sobrescritura;
- existen cambios locales no identificados en una instalación previa;
- la operación exige reorganizar un proyecto existente.

Validaciones obligatorias
Después del clone, confirma:
- ruta absoluta de 00-ia-dos;
- git status limpio;
- remote origin correcto;
- rama main cuando corresponda al clone por defecto;
- existencia de README.md, ORCHESTRATOR.md, AGENTS.md y docs/index.md;
- ningún recurso de proyecto fue creado, movido o modificado.

Reporte final
Entrega:
1. sistema operativo detectado;
2. ruta del workspace;
3. ruta de IA-DOS;
4. comandos ejecutados;
5. resultado de cada validación;
6. conflictos o advertencias;
7. cualquier limitación relevante.

No continúes con la creación o modificación de un proyecto sin una instrucción separada.
```

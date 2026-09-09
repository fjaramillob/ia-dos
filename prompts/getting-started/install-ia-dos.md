# Prompt para instalar o actualizar IA-DOS

Este prompt está pensado para Codex, Claude Code, Antigravity u otro agente con acceso al sistema de archivos y Git.

## Prompt

```text
Objetivo
Mantener una referencia local segura de IA-DOS sin sobrescribir trabajo ni reorganizar proyectos existentes.

Repositorio oficial:
https://github.com/fjaramillob/ia-dos.git

Nombre recomendado:
00-ia-dos

Primero determina si corresponde INSTALAR o ACTUALIZAR.

MODO INSTALAR
Úsalo sólo cuando 00-ia-dos no existe.

Antes de actuar:
1. detecta sistema operativo;
2. identifica la ruta exacta del workspace autorizado;
3. verifica que 00-ia-dos no exista;
4. verifica Git;
5. confirma que el clone no requiere mover o modificar proyectos existentes.

Permitido:
- crear la carpeta raíz del workspace cuando esté autorizada;
- clonar IA-DOS como 00-ia-dos;
- ejecutar Git de solo lectura para verificar.

Prohibido:
- sobrescribir una carpeta existente;
- crear app, Wiki o Exchange como parte de esta instalación;
- mover proyectos;
- modificar archivos de IA-DOS;
- crear commits;
- guardar secretos.

MODO ACTUALIZAR
Úsalo cuando 00-ia-dos ya existe y debe alinearse con origin/main.

Importante:
`git status` antes de `git fetch` NO demuestra que GitHub no tenga commits nuevos.

En Windows, cuando aplique la convención habitual, usa una ruta portable:
Set-Location (Join-Path $HOME "Proyectos\00-ia-dos")

Secuencia normal autorizada:
1. git status --short
2. git remote -v
3. git fetch origin
4. git switch main
5. git rev-list --left-right --count main...origin/main
6. si no hay commits locales/divergencia, git pull --ff-only origin main
7. git rev-parse HEAD
8. git status

Detente si:
- existen cambios locales no identificados;
- origin no coincide con el repositorio oficial;
- main tiene commits locales que origin/main no tiene;
- existe divergencia;
- Git pide resolver merge/rebase;
- la operación requiere reset, clean o force push;
- existe riesgo de sobrescritura.

No uses por rutina:
- git reset --hard;
- git clean;
- merge implícito;
- rebase implícito;
- force push.

Reporte final
Entrega:
- modo utilizado: INSTALAR | ACTUALIZAR;
- sistema operativo;
- ruta de IA-DOS;
- origin verificado;
- estado previo relevante;
- resultado del fetch/divergencia cuando fue actualización;
- SHA final;
- estado final;
- conflictos, advertencias o detención aplicada.

No continúes con creación o modificación de proyectos sin una instrucción separada.
```
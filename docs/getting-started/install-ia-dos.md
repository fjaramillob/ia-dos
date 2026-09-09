# Instalar o actualizar IA-DOS en el workspace local

Esta guía se utiliza cuando el trabajo necesita una referencia local estable de IA-DOS para consultar contratos, plantillas o documentación.

Instalación inicial y actualización de una instalación existente son operaciones distintas.

## Instalación inicial

El único resultado es una referencia local de IA-DOS:

```text
<workspace>/
└── 00-ia-dos/
```

No crea, mueve ni reorganiza recursos del proyecto adoptante.

### Windows PowerShell

```powershell
$Workspace = Join-Path $HOME "Proyectos"
New-Item -ItemType Directory -Force -Path $Workspace | Out-Null
Set-Location $Workspace

if (Test-Path .\00-ia-dos) {
    throw "La carpeta $Workspace\00-ia-dos ya existe. Usa el procedimiento de actualización; no reinstales encima."
}

git clone https://github.com/fjaramillob/ia-dos.git 00-ia-dos
Set-Location .\00-ia-dos

git status
git remote -v
git branch --show-current
git rev-parse HEAD
```

### macOS o Linux

```bash
mkdir -p ~/Proyectos
cd ~/Proyectos

if [ -e ./00-ia-dos ]; then
  echo "00-ia-dos ya existe. Usa el procedimiento de actualización; no reinstales encima." >&2
  exit 1
fi

git clone https://github.com/fjaramillob/ia-dos.git 00-ia-dos
cd 00-ia-dos

git status
git remote -v
git branch --show-current
git rev-parse HEAD
```

## Actualizar una instalación existente

No confundas `git status` con comprobación del remoto: **un working tree limpio antes de `git fetch` no demuestra que GitHub no tenga commits nuevos**.

### Windows PowerShell

Ruta portable recomendada cuando el workspace usa la convención habitual:

```powershell
Set-Location (Join-Path $HOME "Proyectos\00-ia-dos")
```

Secuencia segura:

```powershell
git status --short
git remote -v
git fetch origin
git switch main
git rev-list --left-right --count main...origin/main
git pull --ff-only origin main
git rev-parse HEAD
git status
```

### macOS o Linux

```bash
cd ~/Proyectos/00-ia-dos

git status --short
git remote -v
git fetch origin
git switch main
git rev-list --left-right --count main...origin/main
git pull --ff-only origin main
git rev-parse HEAD
git status
```

## Interpretar divergencia

Después de `git fetch origin`, revisa:

```text
git rev-list --left-right --count main...origin/main
```

Salida conceptual:

```text
0 0
→ alineado

0 N
→ remoto adelantado; `git pull --ff-only` puede avanzar main

N 0
→ commits locales no presentes en origin/main; detenerse

N M
→ divergencia; detenerse
```

Si hay cambios locales sin identificar, commits locales o divergencia, no intentes “arreglar” automáticamente la instalación.

## Acciones que NO son rutina de actualización

No uses por defecto:

- `git reset --hard`;
- `git clean`;
- merge implícito;
- rebase implícito;
- force push;
- sobrescritura de cambios locales.

Si cualquiera de esas acciones pareciera necesaria, detente y revisa el estado real.

## Verificación final

La actualización es correcta cuando:

- `origin` apunta al repositorio oficial;
- `main` no tiene divergencia no resuelta;
- el `git pull --ff-only` completó o no tenía cambios que aplicar;
- `git rev-parse HEAD` identifica el baseline local final;
- `git status` queda limpio;
- no se modificaron proyectos adoptantes.

## Uso cotidiano

Abre únicamente el proyecto y las rutas necesarias. No entregues todo el workspace ni todos los proyectos al coding agent.

Una Task autosuficiente no exige releer el framework completo. Si un Conversation Space fue retomado después de un cambio relevante de IA-DOS, consulta sólo los contratos afectados antes de decidir.

## Siguiente paso

Instalar o actualizar IA-DOS sólo mantiene disponible la referencia local. No crea automáticamente una aplicación, Wiki, Exchange ni otra estructura del proyecto.
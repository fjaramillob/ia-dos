# Instalar IA-DOS en el workspace local

Esta guía se utiliza cuando el Project Orchestrator determina que la siguiente tarea necesita acceso real a repositorios, archivos, Git, plantillas locales o un coding agent.

No es el primer paso del método. El onboarding comienza en conversación y puede avanzar sin instalación local mientras no exista una necesidad de ejecución física.

## Cuándo usar esta guía

Úsala cuando una `Execution Task` requiera una o más de estas capacidades:

- inspeccionar repositorios locales;
- modificar archivos;
- ejecutar comandos o pruebas;
- trabajar con branches, commits o pull requests;
- mantener una Wiki versionada localmente;
- utilizar plantillas de IA-DOS desde un workspace estable.

## Resultado esperado

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

`00-ia-dos/` se instala una sola vez por workspace. No debe copiarse dentro de cada proyecto.

## Requisitos previos

- Git instalado;
- acceso al repositorio oficial;
- una carpeta local estable para el workspace;
- autorización para clonar;
- confirmación de que la ruta no contiene una carpeta `00-ia-dos` que deba conservarse.

## Windows PowerShell

```powershell
$Workspace = Join-Path $HOME "proyectos"
New-Item -ItemType Directory -Force -Path $Workspace | Out-Null
Set-Location $Workspace

if (Test-Path .\00-ia-dos) {
    throw "La carpeta $Workspace\00-ia-dos ya existe. Revisa su contenido antes de continuar."
}

git clone https://github.com/fjaramillob/ia-dos.git 00-ia-dos
Set-Location .\00-ia-dos

git status
git remote -v
git branch --show-current
```

## macOS o Linux

```bash
mkdir -p ~/proyectos
cd ~/proyectos

if [ -e ./00-ia-dos ]; then
  echo "La carpeta ~/proyectos/00-ia-dos ya existe. Revisa su contenido antes de continuar." >&2
  exit 1
fi

git clone https://github.com/fjaramillob/ia-dos.git 00-ia-dos
cd 00-ia-dos

git status
git remote -v
git branch --show-current
```

## Verificación

La instalación es correcta cuando:

- existe `00-ia-dos/`;
- el árbol de trabajo está limpio;
- `origin` apunta al repositorio oficial;
- la rama actual es `main`;
- existen `README.md`, `ORCHESTRATOR.md`, `AGENTS.md` y `docs/index.md`.

## Uso cotidiano

Para una tarea normal, abre únicamente el proyecto y las rutas necesarias. No entregues todo el workspace ni todos los proyectos al coding agent.

## Condiciones de detención

Detén la instalación cuando:

- `00-ia-dos/` ya existe;
- Git solicita credenciales inesperadas;
- el remote no coincide con el repositorio oficial;
- existen cambios locales no identificados;
- la operación podría sobrescribir otro proyecto;
- la ruta elegida expondría repositorios no relacionados.

## Siguiente paso

Regresa a la `Execution Task` que originó la instalación y prepara únicamente los repositorios o rutas que esa tarea necesita.

Según el escenario, continúa con:

- [Crear un proyecto nuevo en el workspace](create-new-project-workspace.md)
- [Incorporar un proyecto existente](incorporate-existing-project-workspace.md)
- [Preparar el handoff de ejecución](execution-handoff.md)

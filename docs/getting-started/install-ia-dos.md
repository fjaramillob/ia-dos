# Instalar IA-DOS en el workspace local

Esta guía se utiliza cuando el Project Orchestrator determina que la siguiente tarea necesita una referencia local estable de IA-DOS para consultar contratos, plantillas o documentación.

No es el primer paso del método. El onboarding comienza en conversación y puede avanzar sin instalación local mientras el acceso remoto o el contrato embebido sean suficientes.

## Cuándo usar esta guía

Úsala cuando el trabajo autorizado necesite una o más de estas capacidades:

- consultar IA-DOS desde un workspace local estable;
- utilizar plantillas locales del framework;
- comparar una adopción con una versión o commit local;
- trabajar sin acceso fiable al repositorio remoto;
- mantener una referencia compartida para varios proyectos del mismo workspace.

Instalar IA-DOS no crea, mueve ni reorganiza recursos del proyecto adoptante.

## Resultado esperado

El único resultado propio de esta guía es una referencia local de IA-DOS:

```text
<workspace>/
└── 00-ia-dos/
```

Los proyectos que ya existan permanecen donde estén. Si el workspace contiene otros recursos, esta instalación no cambia su topología.

`00-ia-dos/` se instala una sola vez por workspace cuando esa referencia local aporta valor. No debe copiarse dentro de cada proyecto.

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

Los comandos usan `~/proyectos` sólo como ejemplo. Sustituye esa ruta por el workspace autorizado; no muevas proyectos existentes para coincidir con el ejemplo.

## Verificación

La instalación es correcta cuando:

- existe `<workspace>/00-ia-dos/` en la ruta autorizada;
- el árbol de trabajo de IA-DOS está limpio;
- `origin` apunta al repositorio oficial;
- la rama actual es `main` cuando se instaló desde la rama por defecto;
- existen `README.md`, `ORCHESTRATOR.md`, `AGENTS.md` y `docs/index.md`;
- no se crearon, movieron ni modificaron recursos de proyectos adoptantes.

## Uso cotidiano

Para una tarea normal, abre únicamente el proyecto y las rutas necesarias. No entregues todo el workspace ni todos los proyectos al coding agent.

La referencia `00-ia-dos/` se consulta sólo cuando aporta; una tarea autosuficiente no exige releer el framework completo.

## Condiciones de detención

Detén la instalación cuando:

- `00-ia-dos/` ya existe;
- la ruta autorizada es ambigua;
- Git solicita credenciales inesperadas;
- el remote no coincide con el repositorio oficial;
- existen cambios locales no identificados en una instalación previa;
- la operación podría sobrescribir otro recurso;
- instalar la referencia exigiría mover o reorganizar un proyecto;
- la ruta elegida expondría repositorios no relacionados.

## Siguiente paso

La instalación sólo deja disponible la referencia local de IA-DOS. No crea automáticamente una aplicación, Wiki, Exchange ni otra estructura del proyecto.

Después vuelve a la unidad que justificó la instalación. Según el escenario, puede corresponder:

- [Crear un proyecto nuevo en el workspace](create-new-project-workspace.md)
- [Incorporar un proyecto existente](incorporate-existing-project-workspace.md)
- [Preparar el handoff de ejecución](execution-handoff.md)

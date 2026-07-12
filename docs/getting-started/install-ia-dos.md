# Instalar IA-DOS en el workspace local

Esta guía explica cómo incorporar IA-DOS una sola vez dentro de un workspace de desarrollo.

La instalación local no es obligatoria para comenzar desde ChatGPT, Gemini, Claude u otro asistente conversacional. Sí es la forma recomendada cuando el proyecto entra en trabajo con repositorios, archivos, Git y coding agents.

## Resultado esperado

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

`00-ia-dos/` se instala una sola vez. No debe copiarse dentro de cada proyecto.

## Requisitos previos

Antes de comenzar, verifica:

- Git instalado;
- acceso a GitHub;
- una carpeta local que utilizarás como workspace;
- que no exista ya una carpeta distinta llamada `00-ia-dos` con contenido que deba conservarse.

## Windows PowerShell

Ejemplo utilizando `C:\proyectos`:

```powershell
New-Item -ItemType Directory -Force -Path C:\proyectos | Out-Null
Set-Location C:\proyectos

if (Test-Path .\00-ia-dos) {
    Write-Error "La carpeta C:\proyectos\00-ia-dos ya existe. Detén la instalación y revisa su contenido."
    exit 1
}

git clone https://github.com/fjaramillob/ia-dos.git 00-ia-dos
Set-Location .\00-ia-dos

git status
git remote -v
git branch --show-current
```

## macOS o Linux

Ejemplo utilizando `~/proyectos`:

```bash
mkdir -p ~/proyectos
cd ~/proyectos

if [ -e ./00-ia-dos ]; then
  echo "La carpeta ~/proyectos/00-ia-dos ya existe. Detén la instalación y revisa su contenido." >&2
  exit 1
fi

git clone https://github.com/fjaramillob/ia-dos.git 00-ia-dos
cd 00-ia-dos

git status
git remote -v
git branch --show-current
```

## Verificaciones

La instalación es correcta cuando:

- existe la carpeta `00-ia-dos/`;
- `git status` indica un árbol de trabajo limpio;
- el remote `origin` apunta a `https://github.com/fjaramillob/ia-dos.git`;
- la rama actual es `main`;
- existen `README.md`, `ORCHESTRATOR.md`, `AGENTS.md` y `docs/index.md`.

## Actualizar IA-DOS

Desde `00-ia-dos/`:

```bash
git status
git pull --ff-only
```

No ejecutes `git pull` si existen cambios locales sin revisar.

Antes de adoptar una nueva versión en un proyecto:

1. revisa `CHANGELOG.md`;
2. identifica cambios de comportamiento u obligaciones;
3. confirma compatibilidad con la estructura del proyecto;
4. actualiza la versión declarada en `.ia-dos.yaml` solo después de aprobar el cambio.

No declares `main`, `latest` o `current` como versión adoptada por un proyecto.

## Abrir el workspace completo o un proyecto

La carpeta `proyectos/` puede utilizarse para administración general.

Para el trabajo cotidiano, abre solamente:

```text
nombre-proyecto/
├── nombre-proyecto-app/
└── nombre-proyecto-wiki/
```

No abras todo `proyectos/` a un coding agent salvo que la tarea requiera explícitamente administración transversal. Esto reduce acceso innecesario, mezcla de contexto y consumo de tokens.

## Condiciones de detención

Detén la instalación y revisa antes de continuar cuando:

- `00-ia-dos/` ya existe;
- Git solicita credenciales inesperadas;
- el remote no apunta al repositorio oficial;
- el clone queda incompleto;
- hay cambios locales no identificados;
- el comando intenta sobrescribir un proyecto existente;
- la ruta elegida contiene repositorios que no deberían quedar disponibles para agentes.

## Siguiente paso

Después de instalar IA-DOS:

1. crea o identifica la carpeta del proyecto;
2. incorpora el repositorio de aplicación sin moverlo a ciegas;
3. crea o conecta la LLM Wiki;
4. documenta cualquier excepción a la estructura recomendada;
5. registra la versión adoptada.
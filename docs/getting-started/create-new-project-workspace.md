# Crear un proyecto nuevo dentro del workspace

Esta guía formaliza un proyecto nuevo dentro del workspace local sin elegir stack, generar una aplicación completa ni inventar arquitectura.

El resultado de este paso es una estructura segura y reconocible para continuar después con la LLM Wiki y el desarrollo.

## Antes de comenzar

Debes contar con:

- un workspace local preparado;
- IA-DOS instalado como `00-ia-dos/` o disponible por referencia;
- un nombre provisional o definitivo para el proyecto;
- una definición inicial obtenida en `00 — Dirección y definición`;
- autorización para crear carpetas y, cuando corresponda, repositorios Git.

No es necesario haber decidido framework, base de datos, proveedor cloud ni arquitectura final.

## Nombre técnico del proyecto

Define un `project-slug` estable para carpetas y repositorios.

Formato recomendado:

```text
nombre-proyecto
```

Reglas:

- minúsculas;
- palabras separadas por guiones;
- sin espacios;
- sin tildes;
- sin caracteres especiales;
- evitar nombres genéricos como `app`, `nuevo` o `proyecto`.

Ejemplos válidos:

```text
tag-cl
junta-fc
control-tesoreria
```

El nombre comercial visible puede ser distinto del `project-slug`.

## Estructura objetivo

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

La carpeta exterior `nombre-proyecto/` agrupa los componentes. Normalmente no debe convertirse en repositorio Git.

## Qué se crea en este paso

### Repositorio de aplicación

```text
nombre-proyecto-app/
└── README.md
```

El `README.md` inicial solo debe declarar:

- nombre del proyecto;
- propósito resumido cuando esté confirmado;
- estado: implementación no iniciada;
- enlace o ruta hacia la wiki;
- advertencia de no asumir stack o arquitectura todavía.

No generes código, dependencias, configuración, `.env`, pipelines ni despliegues.

### Repositorio de wiki

```text
nombre-proyecto-wiki/
└── index.md
```

El `index.md` inicial solo debe declarar:

- nombre del proyecto;
- estado: wiki pendiente de bootstrap;
- fuente inicial: conversación `00 — Dirección y definición`;
- ruta o enlace al repositorio de aplicación;
- siguiente paso: ejecutar la guía de creación de la LLM Wiki.

No completes archivos con contenido supuesto para llenar una estructura.

## Git recomendado

IA-DOS recomienda dos repositorios Git independientes:

```text
nombre-proyecto-app/.git
nombre-proyecto-wiki/.git
```

La inicialización puede realizarse localmente antes de crear remotes.

```bash
git init -b main
```

Crea el primer commit solamente cuando:

- los archivos iniciales fueron revisados;
- la identidad Git está configurada;
- no hay secretos;
- el usuario autorizó el commit.

No crees automáticamente repositorios públicos. La visibilidad de app y wiki debe decidirse de forma independiente.

## Windows PowerShell

Ejemplo estructural:

```powershell
$Workspace = Join-Path $HOME "proyectos"
$Project = "nombre-proyecto"
$ProjectRoot = Join-Path $Workspace $Project
$App = Join-Path $ProjectRoot "$Project-app"
$Wiki = Join-Path $ProjectRoot "$Project-wiki"

if ($Project -notmatch '^[a-z0-9]+(?:-[a-z0-9]+)*$') {
    Write-Error "El project-slug no cumple la convención recomendada."
    exit 1
}

if (Test-Path $ProjectRoot) {
    Write-Error "La carpeta del proyecto ya existe. Detente y revisa su contenido."
    exit 1
}

New-Item -ItemType Directory -Path $App -Force | Out-Null
New-Item -ItemType Directory -Path $Wiki -Force | Out-Null
```

Después crea manualmente los archivos mínimos y revisa su contenido antes de inicializar Git.

## macOS o Linux

Ejemplo estructural:

```bash
WORKSPACE="$HOME/proyectos"
PROJECT="nombre-proyecto"
PROJECT_ROOT="$WORKSPACE/$PROJECT"
APP="$PROJECT_ROOT/$PROJECT-app"
WIKI="$PROJECT_ROOT/$PROJECT-wiki"

if ! printf '%s' "$PROJECT" | grep -Eq '^[a-z0-9]+(-[a-z0-9]+)*$'; then
  echo "El project-slug no cumple la convención recomendada." >&2
  exit 1
fi

if [ -e "$PROJECT_ROOT" ]; then
  echo "La carpeta del proyecto ya existe. Detente y revisa su contenido." >&2
  exit 1
fi

mkdir -p "$APP" "$WIKI"
```

Después crea manualmente los archivos mínimos y revisa su contenido antes de inicializar Git.

## Fuentes de verdad al finalizar

Este paso establece:

| Información | Ubicación |
|---|---|
| Identidad técnica del proyecto | nombre de la carpeta exterior |
| Implementación | `nombre-proyecto-app/` |
| Memoria durable | `nombre-proyecto-wiki/` |
| Método común | `00-ia-dos/` o referencia versionada |
| Dirección conversacional | Project de ChatGPT, Gem o equivalente |

Todavía no establece una arquitectura técnica ni una versión completa de la wiki.

## Verificación

Antes de considerar el proyecto creado, confirma:

- [ ] El `project-slug` es estable y válido.
- [ ] La carpeta exterior se encuentra dentro del workspace elegido.
- [ ] Existen las carpetas app y wiki.
- [ ] La carpeta exterior no es un repositorio Git sin justificación.
- [ ] App y wiki son repositorios separados o existe una excepción documentada.
- [ ] La app no contiene código ni dependencias generadas sin decisión previa.
- [ ] La wiki no presenta propuestas como hechos.
- [ ] No existen secretos.
- [ ] Las rutas absolutas fueron reportadas.
- [ ] El siguiente paso está identificado.

## Condiciones de detención

Detente antes de escribir cuando:

- la carpeta del proyecto ya existe;
- el nombre coincide con otro proyecto;
- la ruta del workspace es ambigua;
- existen repositorios anidados no planificados;
- no está claro si app o wiki deben ser públicas;
- la solicitud implica elegir stack o generar funcionalidades todavía no definidas;
- falta autorización para inicializar Git o crear commits.

## Siguiente paso

Continúa con [Crear la LLM Wiki del proyecto](bootstrap-llm-wiki.md).

La primera tarea hacia un coding agent se prepara después de contar con contexto mínimo, alcance y fuentes de verdad.
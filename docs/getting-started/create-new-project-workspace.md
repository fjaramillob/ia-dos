# Crear un proyecto nuevo dentro del workspace

Esta guía materializa un proyecto nuevo dentro de un workspace local sin elegir stack, generar una aplicación completa ni inventar arquitectura.

La estructura física depende de los recursos que el proyecto realmente necesite. IA-DOS no exige separar app, Wiki o Exchange en repositorios distintos.

## Antes de comenzar

Debes contar con:

- un workspace local elegido;
- IA-DOS disponible por referencia remota o local;
- un nombre provisional o definitivo para el proyecto;
- dirección inicial suficiente desde `00 — Dirección y orquestación` en modo `definición inicial`;
- autorización para crear las carpetas y repositorios que realmente correspondan.

No es necesario haber decidido framework, base de datos, proveedor cloud ni arquitectura final.

## Nombre técnico del proyecto

Define un `project-slug` estable para carpetas y repositorios cuando la estructura local lo necesite.

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

El nombre visible puede ser distinto del `project-slug`.

## Topologías válidas

Una organización útil cuando se desea separar implementación y memoria es:

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

Exchange puede agregarse después como recurso hermano cuando el proyecto lo adopte.

También son válidos:

```text
nombre-proyecto/
└── repositorio-monorepo/
    ├── app/
    └── docs/
```

```text
nombre-proyecto-app/
```

si la siguiente unidad todavía no necesita una Wiki separada.

No crees una carpeta sólo porque aparece en un ejemplo.

## Qué se crea en este paso

Crea únicamente los recursos autorizados.

### Implementación, cuando corresponda

Un repositorio nuevo puede comenzar con:

```text
README.md
```

El README inicial sólo necesita declarar:

- nombre del proyecto;
- propósito resumido cuando esté confirmado;
- estado real, por ejemplo `implementación no iniciada`;
- ubicación de la memoria durable cuando ya exista;
- advertencia de no asumir stack o arquitectura todavía.

No generes código, dependencias, `.env`, pipelines ni despliegues sin una tarea específica.

### Memoria durable, cuando corresponda

Antes de crearla evalúa el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md).

Cuando el proyecto decida crear una Wiki Markdown, usa directamente `templates/wiki-starter/` y [Aplicar las plantillas mínimas de adopción](apply-starter-templates.md).

No crees un `index.md` provisional ni una segunda estructura transitoria que luego deba migrarse.

El starter utiliza:

```text
00-home.md
project-brief.md
status/current-state.md
```

como núcleo inicial, con `decisions/` y `sources/` disponibles para conocimiento durable real.

### Exchange, cuando corresponda

Exchange no forma parte obligatoria del bootstrap de un proyecto nuevo.

Créalo sólo cuando conservar `Execution Task` y `Execution Report` fuera de la conversación aporte una ventaja operacional concreta.

Consulta [Crear o conectar Exchange Protocol v0](bootstrap-exchange.md).

Una estructura posible es:

```text
nombre-proyecto-exch/
├── inbox/
├── outbox/
├── archive/
└── templates/
    ├── TASK.md
    └── REPORT.md
```

No crees `REGISTRY.md`, contador compartido, watcher, trigger ni automatización en v0.

## Git

Cada recurso puede tener su propio repositorio Git, compartir un monorepo o no usar Git todavía, según la decisión del proyecto.

No conviertas la carpeta exterior en repositorio Git por defecto.

Inicializa Git sólo cuando esté autorizado y la topología elegida lo requiera.

```bash
git init -b main
```

Crea un commit sólo cuando:

- los archivos fueron revisados;
- la identidad Git está configurada;
- no hay secretos;
- la tarea autoriza commit.

No crees automáticamente repositorios remotos ni definas su visibilidad sin aprobación.

## Ejemplo PowerShell

Este ejemplo crea sólo una carpeta de proyecto y un recurso de implementación. Agrega otros recursos únicamente cuando hayan sido decididos.

```powershell
$Workspace = Join-Path $HOME "proyectos"
$Project = "nombre-proyecto"
$ProjectRoot = Join-Path $Workspace $Project
$App = Join-Path $ProjectRoot "$Project-app"

if ($Project -notmatch '^[a-z0-9]+(?:-[a-z0-9]+)*$') {
    Write-Error "El project-slug no cumple la convención recomendada."
    exit 1
}

if (Test-Path $ProjectRoot) {
    Write-Error "La carpeta del proyecto ya existe. Detente y revisa su contenido."
    exit 1
}

New-Item -ItemType Directory -Path $App -Force | Out-Null
```

## Ejemplo macOS o Linux

```bash
WORKSPACE="$HOME/proyectos"
PROJECT="nombre-proyecto"
PROJECT_ROOT="$WORKSPACE/$PROJECT"
APP="$PROJECT_ROOT/$PROJECT-app"

if ! printf '%s' "$PROJECT" | grep -Eq '^[a-z0-9]+(-[a-z0-9]+)*$'; then
  echo "El project-slug no cumple la convención recomendada." >&2
  exit 1
fi

if [ -e "$PROJECT_ROOT" ]; then
  echo "La carpeta del proyecto ya existe. Detente y revisa su contenido." >&2
  exit 1
fi

mkdir -p "$APP"
```

## Fuentes de verdad al finalizar

Registra sólo las que existan:

| Información | Recurso |
|---|---|
| Implementación | `[RUTA O URL]` |
| Memoria durable | `[RUTA, URL O NO APLICA]` |
| Backlog | `[RUTA, URL O NO APLICA]` |
| Exchange | `[RUTA, URL O NO APLICA]` |
| Método IA-DOS | `[VERSIÓN / COMMIT / REFERENCIA]` |
| Dirección conversacional | `[PROJECT, GEM O EQUIVALENTE]` |

Exchange no reemplaza backlog ni memoria durable. Si ambos existen, registra cada recurso por separado.

## Verificación

Antes de cerrar:

- [ ] El `project-slug`, si se usa, es estable.
- [ ] No se sobrescribieron carpetas existentes.
- [ ] Sólo se crearon recursos autorizados.
- [ ] No se eligió stack ni arquitectura implícitamente.
- [ ] La memoria, si se creó, usa directamente el starter vigente.
- [ ] Exchange, si se creó, tiene una razón operacional concreta y no contiene automatización asumida.
- [ ] No existen secretos.
- [ ] Git, commits o remotes sólo se usaron cuando estaban autorizados.
- [ ] Las rutas reales fueron reportadas.

## Condiciones de detención

Detente antes de escribir cuando:

- la ruta del workspace sea ambigua;
- exista una carpeta o repositorio en conflicto;
- la topología física no esté decidida y el cambio la haría difícil de revertir;
- la solicitud implique elegir tecnología o generar funcionalidades aún no definidas;
- falte autorización para crear recursos, inicializar Git o realizar commits.

## Siguiente paso

Si el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md) devuelve `BOOTSTRAP REQUIRED`, continúa con [Crear o conectar la memoria durable](bootstrap-llm-wiki.md).

Si el proyecto decidió adoptar Exchange, configúralo con [Crear o conectar Exchange Protocol v0](bootstrap-exchange.md).

Después continúa con la siguiente Planning Task o Execution Task sin crear componentes adicionales por ceremonia.

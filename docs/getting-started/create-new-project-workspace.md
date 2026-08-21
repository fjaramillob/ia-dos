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

Exchange puede agregarse después como recurso hermano cuando una pasarela de archivos aporte valor.

También son válidos monorepos, documentación dentro de la app u otras configuraciones. No crees una carpeta sólo porque aparece en un ejemplo.

## Qué se crea en este paso

Crea únicamente los recursos autorizados.

### Implementación, cuando corresponda

Un repositorio nuevo puede comenzar con `README.md`.

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

### Exchange, cuando corresponda

Exchange no forma parte obligatoria del bootstrap.

Créalo sólo cuando una pasarela de archivos Markdown entre Conversation Agent y Code Agent aporte una ventaja operacional concreta.

Consulta [Crear o conectar Exchange](bootstrap-exchange.md).

Una estructura posible es:

```text
nombre-proyecto-exch/
├── inbox/
├── outbox/
└── archive/
```

No crees templates, IDs, registros, estados o automatización dentro de Exchange. Los artefactos llegan ya construidos por los agentes responsables.

## Git

Cada recurso puede tener su propio repositorio Git, compartir un monorepo o no usar Git todavía, según la decisión del proyecto.

No conviertas la carpeta exterior en repositorio Git por defecto. Inicializa Git sólo cuando esté autorizado y la topología elegida lo requiera.

Crea un commit sólo cuando los archivos fueron revisados, la identidad Git está configurada, no hay secretos y la tarea autoriza commit.

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

Exchange no reemplaza ninguna fuente de verdad; sólo sirve como pasarela de archivos.

## Verificación

Antes de cerrar:

- [ ] El `project-slug`, si se usa, es estable.
- [ ] No se sobrescribieron carpetas existentes.
- [ ] Sólo se crearon recursos autorizados.
- [ ] No se eligió stack ni arquitectura implícitamente.
- [ ] La memoria, si se creó, usa directamente el starter vigente.
- [ ] Exchange, si se creó, sólo contiene la pasarela acordada y no lógica propia.
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

Si el Memory Bootstrap Gate devuelve `BOOTSTRAP REQUIRED`, continúa con [Crear o conectar la memoria durable](bootstrap-llm-wiki.md).

Si se decidió utilizar Exchange, crea o conecta únicamente su pasarela con [Crear o conectar Exchange](bootstrap-exchange.md).

Después continúa con la siguiente Planning Task o Execution Task sin crear componentes adicionales por ceremonia.

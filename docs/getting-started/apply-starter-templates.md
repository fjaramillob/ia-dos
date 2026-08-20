# Aplicar las plantillas mínimas de adopción

Este paso convierte una configuración de proyecto en una adopción reproducible de IA-DOS sin imponer una topología física única.

Las plantillas no deben copiarse sin revisión. Adáptalas al proyecto y completa sólo información confirmada.

## Plantillas disponibles

```text
templates/
├── adoption.template.yaml
├── AGENTS.template.md
└── wiki-starter/
    ├── 00-home.md
    ├── project-brief.md
    ├── AGENTS.md
    ├── status/
    │   └── current-state.md
    ├── decisions/
    │   └── README.md
    └── sources/
        └── README.md
```

El starter ya no crea `tasks/`, `context-packs/`, `log.md` ni una página de arquitectura vacía. Esos elementos aparecen sólo cuando existe una necesidad real.

## Antes de crear la Wiki

Evalúa el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md).

Si la siguiente unidad no depende de conocimiento que sólo vive en conversaciones, no es obligatorio detenerse para instalar una Wiki completa.

Cuando el gate devuelve `BOOTSTRAP REQUIRED`, crea o actualiza sólo el checkpoint durable necesario.

## Destino posible

Una topología válida es:

```text
nombre-proyecto/
├── nombre-proyecto-app/
│   └── AGENTS.md
└── nombre-proyecto-wiki/
    ├── .ia-dos.yaml
    ├── 00-home.md
    ├── project-brief.md
    ├── AGENTS.md
    ├── status/
    │   └── current-state.md
    ├── decisions/
    │   └── README.md
    └── sources/
        └── README.md
```

También son válidos monorepos, documentación dentro de la app u otras configuraciones. No reorganices un proyecto existente sólo para coincidir con este ejemplo.

## Paso 1 — Crear el manifiesto de adopción

Copia:

```text
templates/adoption.template.yaml
```

como `.ia-dos.yaml` en la ubicación adoptada para la memoria o configuración del proyecto.

Completa:

- nombre y slug;
- versión o commit concreto de IA-DOS;
- modelo de adopción;
- Project Orchestrator utilizado;
- rutas o URLs reales de implementación, memoria, backlog y Exchange cuando exista;
- fuente de tareas;
- excepciones reales.

No declares `main`, `latest` o `current` como versión adoptada cuando necesites reproducibilidad.

## Paso 2 — Incorporar `AGENTS.md` en la implementación cuando corresponda

Copia:

```text
templates/AGENTS.template.md
```

hacia el repositorio o directorio donde el coding agent ejecutará cambios.

Adapta sólo reglas reales:

- propósito;
- ubicación de memoria y manifiesto;
- comandos y verificaciones existentes;
- zonas permitidas y prohibidas;
- condiciones de detención.

No agregues comandos, herramientas o rutas que el proyecto no tenga.

## Paso 3 — Crear el checkpoint de Wiki

Copia `templates/wiki-starter/` hacia la ubicación elegida para la memoria Markdown.

Completa primero:

1. `00-home.md`;
2. `project-brief.md`;
3. `status/current-state.md`;
4. `AGENTS.md`;
5. `.ia-dos.yaml` cuando la adopción formal lo requiera.

`decisions/` y `sources/` pueden permanecer sólo con su `README.md` hasta que exista contenido durable real.

No crees arquitectura, producto u operaciones sólo para llenar carpetas.

## Paso 4 — Separar estado de intención

Durante el bootstrap usa estados explícitos:

```text
Implementado
Decidido / aprobado pero no implementado
Pendiente
Fuera de alcance
Desconocido
```

En un proyecto nuevo declara expresamente qué todavía no existe.

En un proyecto existente deriva el estado de evidencia o de fuentes autorizadas. Cuando no haya evidencia suficiente, usa `Desconocido`.

## Paso 5 — Verificar navegación y autoridad

Confirma:

- `00-home.md` permite localizar el conocimiento principal;
- los enlaces Markdown relativos funcionan desde la estructura real;
- `.ia-dos.yaml` utiliza rutas o referencias coherentes;
- la implementación puede localizar la memoria cuando sea necesario;
- la memoria identifica dónde demostrar implementación y trabajo pendiente;
- la fuente de tareas no se duplica dentro de la Wiki;
- Exchange, si existe, no se usa como memoria vigente;
- los agentes no reciben acceso automático a todo el workspace.

## Obsidian

La carpeta de memoria puede abrirse directamente como vault de Obsidian.

No necesitas convertir los enlaces Markdown en wikilinks ni instalar plugins para que IA-DOS funcione.

Si el proyecto decide versionar configuración de `.obsidian/`, esa decisión es local al proyecto. La semántica crítica de la memoria no debe depender de esa configuración.

## Qué no hacen estas plantillas

Las plantillas no:

- eligen stack;
- crean arquitectura;
- generan código;
- crean repositorios remotos;
- crean Exchange automáticamente;
- importan conversaciones históricas;
- convierten TASK/REPORT en memoria;
- sustituyen revisión humana;
- convierten información desconocida en hechos.

## Verificación final

- [ ] El Memory Bootstrap Gate está satisfecho para la siguiente unidad cuando aplica.
- [ ] Existe un punto de entrada claro.
- [ ] `project-brief.md` contiene dirección durable suficiente.
- [ ] `status/current-state.md` refleja realidad comprobada.
- [ ] Los enlaces relativos principales funcionan.
- [ ] La implementación y otras fuentes de verdad están identificadas.
- [ ] No se duplicaron tareas o historial operacional dentro de la Wiki.
- [ ] `.ia-dos.yaml` declara una versión concreta cuando se usa.
- [ ] No existen secretos.
- [ ] No quedan placeholders interpretables como hechos.

## Siguiente paso

Después del bootstrap, continúa con la siguiente Planning Task o Execution Task que originó la necesidad de memoria. No conviertas la instalación de la Wiki en un proyecto paralelo.
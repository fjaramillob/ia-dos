# Preparar el workspace local

El workspace local se prepara cuando una tarea definida en conversación necesita acceso real a repositorios, archivos, Git o un coding agent. No es un requisito previo para iniciar IA-DOS.

La secuencia correcta es:

```text
00 orienta
→ se define una unidad verificable
→ se confirma que requiere ejecución local
→ se prepara sólo el acceso necesario
→ se ejecuta y se devuelve evidencia
```

## Durable topology vs ephemeral execution

Antes de imponer orden visual, distingue dos planos:

- **durable topology**: repositorios canónicos, servicios, datastores, memoria y componentes permanentes;
- **ephemeral execution surface**: branches, worktrees, previews, fixtures, scratch scripts, evidence y entornos temporales.

El segundo plano puede crecer libremente dentro de autoridad. No uses un máximo arbitrario de worktrees o branches. El requisito es que su lifecycle sea claro y no confunda qué es canónico.

Cuando la raíz del proyecto ya no sea autoexplicativa, puede existir un `PROJECT.md` o mapa equivalente basado en `templates/project-map.template.md`.

## Estructura posible

Una organización local útil puede ser:

```text
proyectos/
├── 00-ia-dos/
├── proyecto-a/
│   ├── proyecto-a-app/
│   └── proyecto-a-wiki/
└── proyecto-b/
    └── proyecto-b-monorepo/
```

La ubicación puede ser `$HOME\proyectos` en Windows o `~/proyectos` en macOS y Linux, pero es una convención, no una obligación.

IA-DOS no exige que todos los proyectos adopten la misma topología.

Una estructura con ejecución efímera separada puede ser:

```text
proyecto/
├── PROJECT.md              # opcional: mapa del workspace
├── proyecto-app/           # durable
├── proyecto-wiki/          # durable, si existe
├── _worktrees/             # ephemeral execution
│   └── ...
└── archive/                # cold storage, si existe
```

Los nombres son convenciones opcionales. Lo importante es la separación semántica.

## Principios

- IA-DOS puede mantenerse una sola vez como referencia local compartida cuando esa instalación aporte;
- cada proyecto identifica su implementación y memoria durable cuando exista;
- app y Wiki pueden estar separadas, convivir en un monorepo o usar otra configuración documentada;
- una Wiki separada no se crea por defecto: aplica el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md) cuando la siguiente unidad dependa de memoria conversacional;
- Exchange es opcional y puede vivir como recurso separado cuando el proyecto lo adopte;
- un coding agent recibe sólo los repositorios y rutas necesarios para el outcome actual;
- el agente puede crear superficies efímeras autorizadas sin redefinir topología durable;
- crear un nuevo repositorio, servicio, datastore o componente top-level durable puede requerir gobierno explícito;
- no se mueve un proyecto existente sólo para cumplir una estructura recomendada.

## Proyecto nuevo

Para un producto nuevo, `00 — Dirección y orquestación` trabaja en modo `definición inicial`.

Después crea únicamente los recursos necesarios para la siguiente unidad. Una configuración posible es:

```text
nombre-proyecto/
├── nombre-proyecto-app/
└── nombre-proyecto-wiki/
```

pero también puede comenzar sólo con implementación o usar un monorepo.

La creación física ocurre después de contar con dirección suficiente y autorización para crear las rutas o repositorios involucrados.

## Proyecto existente

Antes de mover o reorganizar, revisa:

- rutas absolutas y relativas;
- variables de entorno relevantes sin exponer secretos;
- scripts y pipelines;
- configuraciones del editor cuando afecten la operación;
- despliegues;
- enlaces entre repositorios;
- accesos o procesos que dependan de rutas actuales.

Cuando mover agregue riesgo sin beneficio operacional, conserva la ubicación actual y adopta por referencia.

## Acceso de agentes

No abras toda la carpeta `proyectos/` como contexto cotidiano. Para una tarea normal, entrega únicamente:

- el repositorio o recurso técnico correspondiente;
- `Contexto durable necesario`;
- las páginas incluidas en `Lectura requerida`, cuando existan;
- la `Execution Task` o `Planning Task`;
- instrucciones locales aplicables.

`Referencias Wiki` no implican lectura automática.

La referencia local de IA-DOS se consulta para contratos, guías, plantillas o cambios de versión cuando sea necesaria; no se entrega completa como contexto de cada ejecución.

## Seguridad

No guardes en IA-DOS, memoria durable ni Exchange:

- contraseñas;
- API keys;
- tokens;
- claves privadas;
- credenciales cloud;
- archivos `.env` con valores reales;
- datos personales sensibles innecesarios.

## Lifecycle de ejecución efímera

Clasifica recursos temporales de forma operacional:

```text
ACTIVE
→ permanece mientras aporta

COMPLETED / MERGED
→ verifica estado
→ retira superficie efímera cuando sea seguro

ABANDONED
→ preserva evidencia durable necesaria
→ retira superficie efímera cuando sea seguro
```

No muevas directorios que sean Git worktrees manualmente sin comprender las referencias Git; usa mecanismos compatibles con Git y verifica working state antes de cleanup.

## Verificación

Antes de ejecutar una tarea, confirma:

- [ ] la ruta del workspace o recurso objetivo es conocida;
- [ ] no se crearon topologías o repositorios innecesarios;
- [ ] implementación, memoria y otros recursos relevantes están identificados cuando existen;
- [ ] el acceso del agente se limita al alcance necesario;
- [ ] no se entregará acceso a proyectos no relacionados;
- [ ] no existen secretos dentro del contexto compartido;
- [ ] la tarea que justificó preparar el workspace sigue vigente.

## Siguiente paso

Continúa con [Instalar IA-DOS en el workspace](install-ia-dos.md) sólo cuando la tarea requiera una referencia local al framework, sus plantillas o sus guías.

Para crear recursos de un producto nuevo usa [Crear un proyecto nuevo dentro del workspace](create-new-project-workspace.md). Para adoptar uno existente usa [Incorporar un proyecto existente](incorporate-existing-project-workspace.md).
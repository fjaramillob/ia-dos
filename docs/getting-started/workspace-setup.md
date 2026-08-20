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

## Principios

- IA-DOS puede mantenerse una sola vez como referencia local compartida cuando esa instalación aporte;
- cada proyecto identifica su implementación y memoria durable cuando exista;
- app y Wiki pueden estar separadas, convivir en un monorepo o usar otra configuración documentada;
- una Wiki separada no se crea por defecto: aplica el [Memory Bootstrap Gate](../foundations/memory-bootstrap-gate.md) cuando la siguiente unidad dependa de memoria conversacional;
- Exchange es opcional y puede vivir como recurso separado cuando el proyecto lo adopte;
- un coding agent recibe sólo los repositorios y rutas necesarios para la tarea actual;
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
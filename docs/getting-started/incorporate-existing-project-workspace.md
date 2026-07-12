# Incorporar un proyecto existente al workspace

Esta guía formaliza un proyecto que ya tiene código, documentación, repositorios o despliegues dentro de un workspace IA-DOS.

El objetivo no es moverlo ni renombrarlo automáticamente. Primero se inspecciona su situación real, se define la estructura de adopción y se documentan las excepciones.

## Antes de comenzar

Debes contar con:

- acceso al proyecto existente;
- una ruta local conocida o un remote confirmado;
- autorización para inspeccionar su estructura;
- un workspace preparado;
- IA-DOS instalado como `00-ia-dos/` o disponible por referencia.

La primera fase debe realizarse en modo lectura.

## Paso 1 — Identificar la realidad actual

Registra:

- nombre del proyecto;
- ruta absoluta local;
- remote o remotes Git;
- rama principal;
- estado del working tree;
- repositorios relacionados;
- documentación existente;
- ubicación de secretos y variables de entorno;
- pipelines y despliegues;
- integraciones externas;
- personas o procesos que dependen de rutas actuales.

No supongas que una carpeta equivale a un solo repositorio.

## Paso 2 — Clasificar la estructura existente

Identifica uno de estos casos:

### Caso A — App y wiki ya están separadas

```text
nombre-proyecto/
├── nombre-proyecto-app/
└── nombre-proyecto-wiki/
```

Verifica que ambos sean repositorios independientes y que la wiki represente el estado actual.

### Caso B — Existe app pero no wiki

```text
nombre-proyecto-app/
```

Mantén la app donde está y crea una wiki hermana solo después de confirmar la ruta objetivo.

### Caso C — App y documentación viven en el mismo repositorio

No separes automáticamente. Evalúa:

- tamaño y complejidad del proyecto;
- enlaces relativos;
- automatizaciones;
- permisos;
- historial Git;
- consumo de contexto;
- utilidad real de separar.

La documentación puede permanecer dentro de la app si separar agrega fricción innecesaria. Registra la excepción.

### Caso D — El proyecto está fuera del workspace recomendado

No lo muevas de inmediato.

Primero revisa:

- rutas absolutas y relativas;
- scripts;
- configuraciones del editor;
- pipelines;
- despliegues;
- workspaces de paquetes;
- accesos de colaboradores;
- integraciones que dependan de la ubicación actual.

Cuando moverlo sea riesgoso, conserva su ubicación y registra la adopción por referencia.

### Caso E — Monorepo

Mantén el monorepo cuando sea una decisión real del proyecto.

Documenta:

- raíz del monorepo;
- paquetes o aplicaciones;
- ubicación de la documentación;
- instrucciones de acceso para agentes;
- excepciones respecto de la estructura app/wiki separada.

## Paso 3 — Elegir el modelo de adopción

La decisión debe quedar en una de estas formas:

### Modelo recomendado

```text
proyectos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

### Modelo con excepción documentada

Ejemplos:

```text
ruta-existente/nombre-proyecto-app/
proyectos/nombre-proyecto/nombre-proyecto-wiki/
```

```text
nombre-proyecto/
└── repositorio-monorepo/
    ├── apps/
    ├── packages/
    └── docs/
```

La excepción debe indicar motivo, impacto y forma de acceso.

## Paso 4 — Incorporar la app sin alterar su historia

Cuando la app ya existe:

- no ejecutes `git init` nuevamente;
- no reemplaces el remote;
- no cambies la rama principal;
- no hagas commits automáticos;
- no muevas archivos para “ordenar” sin una tarea específica;
- no elimines documentación existente antes de sintetizarla.

Si debe clonarse dentro del workspace, utiliza una carpeta vacía y confirma el nombre objetivo antes de ejecutar `git clone`.

## Paso 5 — Crear o conectar la wiki

Si no existe una wiki:

1. crea la carpeta hermana recomendada o una ubicación alternativa documentada;
2. inicializa Git solo con autorización;
3. crea un `index.md` mínimo;
4. registra que la wiki está pendiente de bootstrap;
5. continúa con la guía [Crear la LLM Wiki del proyecto](bootstrap-llm-wiki.md).

La wiki inicial debe construirse desde evidencia del repositorio y del responsable del proyecto.

## Paso 6 — Registrar la adopción

Al finalizar, deben quedar identificados:

| Elemento | Registro mínimo |
|---|---|
| Proyecto | nombre y `project-slug` |
| App | ruta y remote |
| Wiki | ruta y remote, cuando exista |
| IA-DOS | versión o referencia adoptada |
| Task source | GitHub Issues o mecanismo elegido |
| Excepciones | motivo y efecto |
| Project Orchestrator | espacio conversacional utilizado |

La declaración formal se incorporará después mediante `.ia-dos.yaml`.

## Verificación

Antes de considerar el proyecto incorporado, confirma:

- [ ] La app conserva su historia Git.
- [ ] Los remotes fueron verificados.
- [ ] No se movieron archivos sin autorización.
- [ ] La ruta de la app está documentada.
- [ ] La wiki existe o su creación está planificada.
- [ ] La separación app/wiki fue adoptada o existe una excepción documentada.
- [ ] El Project Orchestrator conoce la ubicación de app y wiki.
- [ ] No se expusieron secretos.
- [ ] Las rutas absolutas fueron reportadas.
- [ ] El siguiente paso está identificado.

## Condiciones de detención

Detente cuando:

- el working tree tiene cambios no identificados;
- el remote no coincide con lo esperado;
- existen varios repositorios y no está clara su relación;
- mover el proyecto puede romper rutas, pipelines o despliegues;
- no está clara la ubicación de secretos;
- la estructura actual contradice la documentación disponible;
- falta autorización para clonar, mover, inicializar Git o crear archivos;
- no puede determinarse cuál es la fuente de verdad de la implementación.

## Siguiente paso

Continúa con la creación o revisión de la LLM Wiki y registra el estado real del proyecto antes de delegar cambios complejos.
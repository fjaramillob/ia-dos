# Modelo de adopción

IA-DOS se adopta por proyecto. No se copia completo dentro de cada repositorio.

## Relación entre IA-DOS y un proyecto

```text
IA-DOS
    define cómo trabajar

Project Orchestrator
    dirige conversaciones y prepara trabajo

Proyecto
    define qué construir, para quién y bajo qué decisiones
```

Cada proyecto define sus propias fuentes y puede mantener, según necesidad:

- implementación;
- memoria durable;
- decisiones;
- Conversation Spaces;
- Execution Cells;
- backlog o sistema de seguimiento;
- Exchange;
- riesgos e historial.

Ninguno de estos elementos exige por sí solo una topología física concreta.

## Estructura recomendada, no obligatoria

Una organización local válida es:

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    ├── nombre-proyecto-wiki/
    └── nombre-proyecto-exch/   # opcional
```

Separar implementación, memoria durable e intercambio de archivos puede facilitar autoridad y consumo selectivo de contexto. Sin embargo, IA-DOS no exige repositorios independientes.

Un proyecto puede utilizar:

- varios repositorios separados;
- un monorepo;
- documentación dentro del mismo repositorio;
- una wiki privada o exclusivamente local;
- otro mecanismo de memoria durable;
- Exchange dentro o fuera del repositorio principal;
- ningún Exchange cuando no aporte valor.

La excepción o configuración elegida debe documentarse cuando afecte la forma de trabajo.

## Instalar una vez

Cuando se desea una referencia local, IA-DOS puede clonarse una sola vez como:

```text
proyectos/00-ia-dos/
```

Desde esa ubicación pueden consultarse documentación, prompts, plantillas y cambios entre versiones.

IA-DOS no se clona nuevamente dentro de cada aplicación o Wiki.

## Consumir por referencia

Un Project de ChatGPT, un Gem de Gemini, un Project de Claude u otro asistente puede consumir IA-DOS mediante:

- acceso al repositorio canónico;
- archivos cargados como contexto;
- una versión publicada;
- `ORCHESTRATOR.md` o instrucciones persistentes adoptadas;
- una referencia local compartida.

Clonar IA-DOS no es requisito técnico para utilizar el método desde un asistente conversacional.

## Adoptar por proyecto

Cada proyecto incorpora sólo los elementos que necesita. Entre los artefactos y recursos disponibles se encuentran:

- memoria durable o LLM Wiki;
- `.ia-dos.yaml` mediante `templates/adoption.template.yaml`;
- instrucciones para el Project Orchestrator;
- `AGENTS.md` para coding agents;
- Planning Tasks y Execution Tasks;
- Execution Cells cuando exista ejecución recurrente;
- Exchange cuando una pasarela de archivos Markdown entre agentes aporte valor;
- guardrails y verificaciones específicas del proyecto.

El trabajo cotidiano debe utilizar las fuentes del proyecto y transportar sólo el contexto necesario. No es necesario cargar IA-DOS completo ni toda la memoria durable en cada conversación o tarea.

## Exchange no es un requisito de adopción

Exchange se incorpora únicamente cuando resuelve una necesidad operacional concreta.

No define qué artefactos pueden existir ni cuáles deben circular. Sólo almacena y pone a disposición archivos `.md` ya construidos por los agentes.

Una adopción puede verse así:

```text
Backlog / Issues
→ qué queda por hacer

Conversation Agent
→ construye el artefacto y define su identidad

Exchange
→ pasa el .md hacia el otro agente y recibe el .md de retorno

Wiki / memoria durable
→ qué sabemos que es verdad ahora

Implementación
→ qué está materializado
```

Cuando Exchange no aporta valor, declara `resources.exchange: NO_APLICA` o simplemente no lo incorpores si el proyecto no utiliza manifiesto.

Consulta [Crear o conectar Exchange](../getting-started/bootstrap-exchange.md).

## Fronteras de autoridad

Cuando esos componentes existan:

```text
Conversation Spaces
→ gobierno y razonamiento activo

Execution Cells
→ continuidad operacional del coding agent

memoria durable
→ conocimiento vigente y confirmado

Exchange
→ pasarela pasiva de archivos Markdown

backlog
→ trabajo pendiente

implementación
→ estado materializado
```

Exchange no sustituye backlog, memoria durable, implementación ni contrato de artefactos.

## Visibilidad y seguridad

Los repositorios y la memoria pueden ser públicos o privados según la naturaleza del proyecto.

La memoria durable y Exchange no deben contener secretos, contraseñas, API keys ni credenciales.

Al compartir repositorios o archivos con asistentes externos, la persona responsable debe revisar qué información está exponiendo y qué operaciones autoriza.

## Versión adoptada

Cada proyecto debe declarar qué versión o commit de IA-DOS utiliza cuando necesite una adopción reproducible.

Usa `templates/adoption.template.yaml` como punto de partida cuando corresponda.

Los artefactos que atraviesan Exchange conservan el contrato con el que fueron construidos. Exchange no los transforma cuando IA-DOS evoluciona.

Los proyectos no reciben cambios del framework de forma silenciosa. Cada actualización debe revisarse antes de adoptarse.

No se recomienda declarar `main`, `latest` o `current` como versión adoptada cuando se requiera reproducibilidad.

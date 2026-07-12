# Crear la LLM Wiki del proyecto

La LLM Wiki es la memoria durable del proyecto. Su función es permitir que personas y asistentes comprendan qué se está construyendo, cuál es su estado real, qué decisiones están vigentes y dónde encontrar las fuentes.

No reemplaza el código, los issues ni los pull requests. Tampoco debe convertirse en una copia de todo el repositorio.

## Cuándo crearla

La wiki debe crearse:

- después de la primera definición de un proyecto nuevo;
- al adoptar un proyecto existente que no tiene memoria estructurada;
- cuando la documentación actual está dispersa o desactualizada;
- antes de aumentar el número de agentes o conversaciones;
- antes de delegar tareas complejas que dependen de decisiones históricas.

## Conversación recomendada

El Project Orchestrator debe crear o utilizar una conversación dedicada:

```text
90 — Wiki y memoria
```

Esta conversación no toma por sí sola decisiones de producto o arquitectura. Su función es sintetizar, ordenar, enlazar y mantener el conocimiento confirmado.

## Estructura mínima recomendada

```text
nombre-proyecto-wiki/
├── index.md
├── project-brief.md
├── current-state.md
├── architecture.md
├── log.md
├── AGENTS.md
├── .ia-dos.yaml
│
├── decisions/
│   └── README.md
│
├── tasks/
│   └── README.md
│
├── sources/
│   └── README.md
│
└── context-packs/
    └── core.md
```

Se pueden agregar nuevas carpetas cuando exista una necesidad real. No se debe crear una taxonomía extensa antes de tener contenido.

## Función de cada archivo

### `index.md`

Punto de entrada y mapa de la wiki.

Debe indicar:

- qué contiene la wiki;
- qué archivos son fundamentales;
- cuál es el estado general;
- cómo navegarla;
- dónde está el repositorio de aplicación.

### `project-brief.md`

Resume:

- propósito;
- usuario;
- problema;
- propuesta de valor;
- alcance;
- fuera de alcance;
- comportamiento esperado;
- dirección visual cuando corresponda;
- restricciones.

### `current-state.md`

Describe qué existe hoy.

Debe distinguir:

```text
Implementado
Parcialmente implementado
Planificado
Deprecado
Desconocido
```

En un proyecto nuevo puede indicar claramente que todavía no existe una implementación.

### `architecture.md`

Describe la arquitectura vigente o, en un proyecto nuevo, la arquitectura propuesta confirmada.

Debe evitar presentar diagramas o componentes hipotéticos como si estuvieran implementados.

### `decisions/`

Contiene decisiones durables.

Cada decisión debe indicar:

- contexto;
- decisión;
- alternativas consideradas;
- consecuencias;
- fecha;
- estado.

### `tasks/`

Se utiliza cuando el proyecto decide conservar `Execution Tasks` en la wiki.

Cuando GitHub Issues es la fuente canónica, esta carpeta puede contener solamente un índice o referencias.

### `sources/`

Contiene o referencia materiales de origen:

- documentos;
- enlaces;
- reportes;
- investigaciones;
- capturas;
- notas sin sintetizar.

Una fuente no se considera automáticamente una decisión vigente.

### `context-packs/core.md`

Contiene el contexto transversal mínimo para asistentes y agentes:

- propósito;
- usuario principal;
- estado actual resumido;
- restricciones;
- decisiones vigentes relevantes;
- ubicación de las fuentes de verdad.

Debe mantenerse pequeño.

### `AGENTS.md`

Explica cómo deben trabajar los agentes dentro de la wiki.

Debe exigir:

- no inventar información;
- enlazar fuentes;
- distinguir hechos y propuestas;
- evitar duplicación;
- actualizar `log.md` cuando corresponda;
- no guardar secretos.

### `.ia-dos.yaml`

Declara la adopción de IA-DOS.

Ejemplo conceptual:

```yaml
ia_dos:
  version: "0.1.0-alpha.1"
  source: "https://github.com/fjaramillob/ia-dos"

project:
  name: "nombre-proyecto"
  app: "../nombre-proyecto-app"
  wiki: "."

adoption:
  model: "separate-app-and-wiki"
  task_source: "github-issues"
  exceptions: []
```

La estructura definitiva de este archivo se entregará como plantilla versionada.

## Proyecto nuevo

Para un proyecto nuevo, la wiki se construye desde decisiones confirmadas en la conversación de dirección.

Debe registrar:

- qué se quiere construir;
- qué todavía no está decidido;
- qué no existe;
- cuál será el primer incremento;
- qué supuestos necesitan validación.

No debe inventar una arquitectura completa para llenar el archivo.

## Proyecto existente

Para un proyecto existente, la wiki debe construirse desde evidencia.

El orquestador puede solicitar a un coding agent una inspección en modo lectura con objetivos como:

- identificar stack y estructura;
- localizar puntos de entrada;
- describir módulos;
- detectar pruebas;
- enumerar integraciones;
- localizar documentación;
- registrar contradicciones;
- no modificar archivos.

El reporte se utiliza como fuente para la wiki, pero debe revisarse antes de considerarlo definitivo.

## Repositorio separado o documentación interna

IA-DOS recomienda con fuerza:

```text
nombre-proyecto/
├── nombre-proyecto-app/
└── nombre-proyecto-wiki/
```

La wiki puede ser un repositorio Git independiente, privado, público o exclusivamente local.

Un proyecto puede mantenerla dentro del repositorio de aplicación cuando:

- es pequeño;
- ya utiliza un monorepo;
- separar repositorios agregaría fricción innecesaria;
- existe una razón documentada.

## Uso desde ChatGPT, Gemini o Claude

El Project Orchestrator debe recibir acceso a la wiki o a los archivos necesarios.

No debe cargar todos los documentos en cada conversación.

Debe utilizar:

```text
CORE
+
un Context Pack principal
+
opcionalmente un Context Pack secundario
```

Las decisiones tomadas en chats deben volver a la wiki cuando sean durables.

## Mantenimiento

La wiki debe actualizarse cuando:

- cambia el comportamiento del producto;
- cambia la arquitectura;
- se toma una decisión durable;
- se identifica un riesgo relevante;
- una tarea invalida información anterior;
- aparece una contradicción;
- una propuesta pasa a implementarse.

No necesita actualizarse por cada conversación ni por cada commit menor.

## Verificación

Antes de considerar la wiki inicial terminada, verifica:

- [ ] Existe un punto de entrada claro.
- [ ] El propósito se entiende.
- [ ] El estado actual no confunde planes con implementación.
- [ ] La arquitectura indica qué es vigente y qué es propuesta.
- [ ] Las decisiones importantes tienen destino.
- [ ] Las fuentes están identificadas.
- [ ] Los agentes tienen instrucciones.
- [ ] Existe un `CORE` pequeño.
- [ ] No contiene secretos.
- [ ] Una persona o asistente puede retomar el proyecto sin leer chats anteriores.

## Resultado esperado

La LLM Wiki debe permitir que el Project Orchestrator y los coding agents sepan dónde están parados, qué información pueden confiar, qué falta por decidir y qué contexto necesitan para la siguiente tarea.

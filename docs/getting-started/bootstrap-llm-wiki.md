# Crear la LLM Wiki del proyecto

La LLM Wiki es la memoria durable del proyecto. Permite que personas y asistentes comprendan qué se está construyendo, cuál es su estado real, qué decisiones están vigentes y dónde encontrar las fuentes.

No reemplaza el código, los issues ni los pull requests. Tampoco debe convertirse en una copia completa del repositorio, una auditoría permanente ni un duplicado del historial de chats.

## Principios LLM Wiki

La implementación de IA-DOS está inspirada en la propuesta **LLM Wiki** de Andrej Karpathy: memoria durable en Markdown, navegable, versionada con Git y separada de las conversaciones.

La wiki debe:

- compilar conocimiento de alta señal, no acumular documentos sin procesar;
- tener un punto de entrada claro;
- dividir el conocimiento en páginas pequeñas y enlazables;
- separar fuentes, hechos, propuestas, decisiones y estado;
- enlazar páginas relacionadas;
- mantenerse versionada con Git;
- actualizarse progresivamente cuando cambia el proyecto;
- permitir cargar `CORE` y solo las páginas relevantes para cada tarea;
- permitir retomar el proyecto sin depender del historial de chats.

IA-DOS agrega encima de estos principios:

- estado explícito de implementación;
- ADRs o decisiones durables;
- `Execution Tasks`;
- Context Packs;
- fuentes de verdad;
- verificación con evidencia.

Esto es una implementación inspirada y compatible con esos principios, no una distribución oficial del sistema de Karpathy.

## Principio operativo

La wiki se **instala temprano y se puebla progresivamente**.

Su propósito inicial no es documentar todo el proyecto. Es ofrecer una estructura mínima y estable para que el Project Orchestrator, Codex, Antigravity, Claude Code u otro coding agent sepan:

- qué proyecto están leyendo;
- qué está confirmado;
- qué existe realmente;
- qué falta decidir;
- dónde están las fuentes;
- qué contexto deben cargar para la siguiente tarea.

No detengas el primer vertical slice para completar documentación sin evidencia.

## Cuándo crearla o conectarla

Créala o conéctala:

- después de la primera definición de un proyecto nuevo;
- al adoptar un proyecto existente sin memoria estructurada;
- antes de delegar tareas que dependan de historia o decisiones previas;
- antes de aumentar significativamente el número de agentes o conversaciones;
- cuando la documentación existente no permite saber con claridad dónde está parado el proyecto.

## `90 — Wiki y memoria` es opcional

No es obligatorio abrir `90 — Wiki y memoria` para instalar la wiki inicial.

La estructura mínima puede crearse mediante una tarea documental acotada usando decisiones ya confirmadas en `00`.

Abre una conversación separada cuando exista trabajo real de:

- síntesis;
- contradicciones;
- consolidación de decisiones durables;
- mantenimiento documental;
- recuperación de una wiki desordenada;
- preparación de contexto para varios agentes.

```text
90 — Wiki y memoria
```

`90` ordena y mantiene conocimiento confirmado. No debe transformarse en una auditoría exhaustiva previa al desarrollo ni tomar por sí sola decisiones de producto o arquitectura.

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
├── tasks/
│   └── README.md
├── sources/
│   └── README.md
└── context-packs/
    └── core.md
```

Esta es una estructura base, no una obligación de llenar todos los archivos de inmediato.

Agrega nuevas carpetas solo cuando exista contenido y una necesidad real. No crees páginas receptoras, plantillas o secciones vacías solo para anticipar conversaciones futuras.

## Poblamiento inicial mínimo

Al comenzar, basta con poblar:

- `index.md`;
- `project-brief.md`;
- `current-state.md`;
- `AGENTS.md`;
- `.ia-dos.yaml`;
- `context-packs/core.md`.

`architecture.md`, ADRs, tareas, fuentes y otras páginas se completan cuando exista evidencia o una decisión real que registrar.

## Función de cada archivo

### `index.md`

Punto de entrada y mapa de navegación. Debe indicar qué contiene la wiki, cuáles son los archivos fundamentales, estado general y ubicación del repositorio de aplicación.

### `project-brief.md`

Resume propósito, usuario, problema, propuesta de valor, alcance, fuera de alcance, comportamiento esperado y restricciones conocidas.

Puede construirse desde `templates/project-intake-brief.template.md`, un documento adjunto o una síntesis de la conversación `00`.

### `current-state.md`

Describe qué existe hoy y distingue:

```text
Implementado
Parcialmente implementado
Planificado
Deprecado
Desconocido
```

En un proyecto nuevo debe indicar claramente que todavía no existe implementación cuando esa sea la evidencia.

### `architecture.md`

Describe arquitectura vigente o una propuesta confirmada. No presenta componentes hipotéticos como implementados. Puede permanecer mínimo hasta que `20 — Arquitectura y stack` produzca una decisión suficiente.

### `decisions/`

Contiene decisiones durables con contexto, decisión, alternativas, consecuencias, fecha y estado.

### `tasks/`

Se utiliza cuando la fuente canónica de `Execution Tasks` está en la wiki. Si GitHub Issues es la fuente canónica, conserva solo índices o referencias.

### `sources/`

Contiene o referencia documentos, enlaces, reportes, investigaciones, capturas y notas sin sintetizar. Una fuente no se considera automáticamente una decisión vigente.

### `context-packs/core.md`

Conserva el contexto transversal mínimo:

- propósito;
- usuario principal;
- estado actual resumido;
- restricciones;
- decisiones vigentes relevantes;
- ubicación de fuentes de verdad.

Debe mantenerse pequeño.

### `AGENTS.md`

Define cómo trabajan los agentes en la wiki: no inventar información, enlazar fuentes, distinguir hechos y propuestas, evitar duplicación, actualizar `log.md` cuando corresponda y no guardar secretos.

### `.ia-dos.yaml`

Declara la adopción de IA-DOS, versión o commit utilizado, rutas, modelo de adopción y fuente canónica de tareas. Usa `templates/adoption.template.yaml`.

## Proyecto nuevo

Instala primero la estructura mínima y construye la wiki desde decisiones confirmadas en `00 — Dirección y definición`.

Registra:

- qué se quiere construir;
- qué todavía no está decidido;
- qué no existe;
- cuál será el primer incremento;
- qué supuestos necesitan validación.

No inventes arquitectura para completar archivos ni detengas el primer vertical slice para llenar la wiki.

## Proyecto existente

Construye la wiki desde evidencia:

- inspección del repositorio en modo lectura;
- README, configuración, dependencias y estructura;
- documentación existente;
- issues y pull requests relevantes;
- conversación con la persona responsable;
- registro de contradicciones y desconocidos.

Un coding agent puede inspeccionar y reportar, pero el reporte debe revisarse antes de considerarlo definitivo.

No conviertas la adopción inicial en una reorganización total. Primero instala el punto de entrada, el estado y las fuentes de verdad; luego normaliza solo lo que realmente obstaculiza el trabajo.

## Repositorio separado o documentación interna

IA-DOS recomienda con fuerza:

```text
nombre-proyecto/
├── nombre-proyecto-app/
└── nombre-proyecto-wiki/
```

La wiki puede permanecer dentro del repositorio de aplicación cuando el proyecto es pequeño, ya utiliza monorepo o la separación agrega fricción injustificada. Documenta la excepción.

## Uso desde ChatGPT, Gemini o Claude

El Project Orchestrator debe recibir acceso a la wiki o a los archivos necesarios.

No cargues toda la wiki en cada conversación. Usa:

```text
CORE
+
un Context Pack principal
+
opcionalmente uno secundario
```

Las decisiones durables tomadas en chats deben volver a la wiki.

## Poblamiento progresivo y mantenimiento

Producto, Arquitectura, Ejecución y Verificación deben devolver a la wiki únicamente decisiones, estado, evidencia y aprendizaje durable.

Actualiza la wiki cuando:

- cambia el comportamiento del producto;
- cambia la arquitectura;
- se toma una decisión durable;
- se identifica un riesgo relevante;
- una tarea invalida información anterior;
- aparece una contradicción;
- una propuesta pasa a implementarse.

No necesita actualizarse por cada conversación o commit menor.

## Verificación

Antes de considerar la wiki inicial utilizable, verifica:

- [ ] Existe un punto de entrada claro.
- [ ] El propósito se entiende.
- [ ] El estado no confunde planes con implementación.
- [ ] Las decisiones importantes tienen destino.
- [ ] Las fuentes están identificadas.
- [ ] Existe un `CORE` pequeño.
- [ ] Los agentes tienen instrucciones.
- [ ] No contiene secretos.
- [ ] Puede retomarse sin leer chats anteriores.

No es necesario que todas las páginas estén completas.

## Resultado esperado

La LLM Wiki debe permitir que el Project Orchestrator y los coding agents sepan dónde están parados, qué información pueden confiar, qué falta decidir y qué contexto necesitan para la siguiente tarea.
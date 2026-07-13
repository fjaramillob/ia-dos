# Crear la LLM Wiki del proyecto

La LLM Wiki es la memoria durable del proyecto. Permite que personas y asistentes comprendan qué se está construyendo, cuál es su estado real, qué decisiones están vigentes y dónde encontrar las fuentes.

No reemplaza el código, los issues ni los pull requests. Tampoco debe convertirse en una copia completa del repositorio o del historial de chats.

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

## Cuándo crearla

Créala:

- después de la primera definición de un proyecto nuevo;
- al adoptar un proyecto existente sin memoria estructurada;
- cuando la documentación está dispersa o desactualizada;
- antes de aumentar el número de agentes o conversaciones;
- antes de delegar tareas complejas que dependen de historia o decisiones previas.

## Conversación recomendada

Utiliza una conversación separada:

```text
90 — Wiki y memoria
```

La conversación `00` puede preparar una síntesis candidata, pero no debe simular `90` como una sección dentro del mismo chat cuando la plataforma permite conversaciones separadas.

`90` sintetiza, ordena, enlaza y mantiene conocimiento confirmado. No toma por sí sola decisiones de producto o arquitectura.

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

Agrega nuevas carpetas solo cuando exista contenido y una necesidad real.

## Función de cada archivo

### `index.md`

Punto de entrada y mapa de navegación. Debe indicar qué contiene la wiki, cuáles son los archivos fundamentales, estado general y ubicación del repositorio de aplicación.

### `project-brief.md`

Resume propósito, usuario, problema, propuesta de valor, alcance, fuera de alcance, comportamiento esperado, dirección visual y restricciones.

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

Describe arquitectura vigente o una propuesta confirmada. No presenta componentes hipotéticos como implementados.

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

Construye la wiki desde decisiones confirmadas en `00 — Dirección y definición`.

Registra:

- qué se quiere construir;
- qué todavía no está decidido;
- qué no existe;
- cuál será el primer incremento;
- qué supuestos necesitan validación.

No inventes arquitectura para completar archivos.

## Proyecto existente

Construye la wiki desde evidencia:

- inspección del repositorio en modo lectura;
- README, configuración, dependencias y estructura;
- documentación existente;
- issues y pull requests relevantes;
- conversación con la persona responsable;
- registro de contradicciones y desconocidos.

Un coding agent puede inspeccionar y reportar, pero el reporte debe revisarse antes de considerarlo definitivo.

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

## Mantenimiento

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

Antes de considerar la wiki inicial terminada, verifica:

- [ ] Existe un punto de entrada claro.
- [ ] El propósito se entiende.
- [ ] El estado no confunde planes con implementación.
- [ ] La arquitectura distingue vigente y propuesta.
- [ ] Las decisiones importantes tienen destino.
- [ ] Las fuentes están identificadas.
- [ ] Las páginas son pequeñas y enlazables.
- [ ] Existe un `CORE` pequeño.
- [ ] Los agentes tienen instrucciones.
- [ ] No contiene secretos.
- [ ] Puede retomarse sin leer chats anteriores.

## Resultado esperado

La LLM Wiki debe permitir que el Project Orchestrator y los coding agents sepan dónde están parados, qué información pueden confiar, qué falta decidir y qué contexto necesitan para la siguiente tarea.
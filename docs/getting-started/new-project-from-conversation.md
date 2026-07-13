# Iniciar un proyecto nuevo desde la capa conversacional

Este recorrido sirve para comenzar un producto objetivo nuevo desde un Project de ChatGPT, Gem de Gemini, Project de Claude o entorno equivalente.

## 1. Configurar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md`.

Entrega como conocimiento:

1. `bundles/ia-dos-project-orchestrator-pack.md`, especialmente cuando la plataforma no pueda navegar GitHub;
2. una descripción inicial, PDF, documento o `templates/project-intake-brief.template.md`;
3. cualquier fuente disponible: notas, referencias, restricciones, diseños o sistemas relacionados.

El usuario no tiene que completar un formulario exhaustivo. El asistente debe extraer primero lo que ya está en las fuentes y preguntar solo por vacíos importantes.

## 2. Confirmar que el producto objetivo es nuevo

Clasifica el producto que se quiere construir, no los sistemas anteriores mencionados como contexto.

Un sistema anterior, migración selectiva, reconstrucción o producto de referencia no convierte automáticamente al producto objetivo en existente.

El producto objetivo es nuevo cuando no existe evidencia propia de implementación como código, despliegue, usuarios, infraestructura o integraciones activas.

## 3. Primera conversación: `00 — Dirección y definición`

Comprende progresivamente:

- propósito;
- usuario principal;
- problema;
- resultado esperado;
- alcance inicial y fuera de alcance;
- funcionamiento y flujos;
- dirección visual;
- activos que ya existen;
- sistemas relacionados y su relación;
- restricciones;
- decisiones confirmadas;
- supuestos y preguntas abiertas;
- criterios de éxito.

Distingue hechos, preferencias, supuestos, propuestas y decisiones. No repitas preguntas ya respondidas por los documentos.

No selecciones stack ni pidas construir la aplicación completa antes de contar con decisiones suficientes.

## 4. Resultado de `00`

Produce una síntesis estructurada con:

- propósito;
- usuario;
- problema;
- alcance y fuera de alcance;
- comportamiento esperado;
- dirección visual;
- activos disponibles;
- sistemas relacionados;
- restricciones;
- decisiones;
- supuestos;
- preguntas abiertas;
- siguiente paso.

No afirmes que existe una aplicación, arquitectura o integración que no haya sido creada.

## 5. Crear `90 — Wiki y memoria`

Cuando la definición sea suficiente, propón una conversación separada:

```text
90 — Wiki y memoria
```

No simules `90` como una sección dentro de `00` cuando la plataforma permita conversaciones separadas.

La wiki se construye siguiendo `bootstrap-llm-wiki.md` y los principios LLM Wiki: Markdown navegable, páginas pequeñas, enlaces, Git, alta señal y separación entre fuentes, hechos, propuestas, decisiones y estado.

## 6. Conversation Spaces progresivos

Comienza con:

```text
00 — Dirección y orquestación
90 — Wiki y memoria
```

Cuando empiece el desarrollo:

```text
30 — Ejecución y desarrollo
```

Agrega `10 — Producto y UX`, `20 — Arquitectura y datos`, `40 — QA y seguridad` u otros espacios solo cuando exista actividad recurrente o mezcla real de contexto.

## 7. Preparar el entorno local

Cuando el proyecto entre en desarrollo:

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

La capa conversacional puede existir antes de estas carpetas.

## 8. Primera salida hacia desarrollo

Prepara una `Execution Task` pequeña, por ejemplo:

- inicializar la aplicación con un stack ya decidido;
- crear estructura base;
- construir un primer flujo vertical verificable;
- inspeccionar una decisión técnica antes de implementarla.

La tarea debe incluir contexto mínimo, alcance, fuera de alcance, criterios, pruebas y condiciones de detención.

## Resultado esperado

- Project Orchestrator configurado;
- descripción inicial suficiente;
- producto objetivo clasificado correctamente;
- definición inicial estructurada;
- LLM Wiki mínima;
- conversaciones mínimas;
- primera tarea acotada.
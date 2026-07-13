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

## 4. Ritmo y gestión de decisiones

Por defecto, resuelve una decisión principal por turno.

Cuando propongas alternativas:

- márcalas como propuestas no confirmadas;
- explica brevemente sus efectos;
- evita inventar mecanismos detallados no presentes en las fuentes;
- combina criterios complementarios en vez de forzar elecciones artificiales;
- ofrece una recomendación simple cuando ayude al usuario.

Cuando el usuario confirme una propuesta, reclasifícala como `Decisión de trabajo confirmada en conversación`.

No la presentes de nuevo como pendiente salvo que aparezca nueva evidencia, una contradicción o el usuario la reabra.

Una decisión solo se vuelve durable cuando queda registrada en `90 — Wiki y memoria` o en un ADR.

Nunca describas al usuario como bloqueo. Utiliza `Pendiente de definición`, `Dependencia externa` o `Condición de detención`.

## 5. Resultado de `00`

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
- decisiones de trabajo confirmadas;
- propuestas pendientes;
- supuestos;
- preguntas abiertas;
- siguiente paso.

No afirmes que existe una aplicación, arquitectura o integración que no haya sido creada.

El bloque de configuración inicial y la instrucción para renombrar la conversación se muestran solo en la primera respuesta.

## 6. Gate de salida de `00`

No cierres `00` ni propongas `90 — Wiki y memoria` hasta que exista una síntesis suficiente y el usuario la apruebe explícitamente.

Verifica al menos:

- propósito y usuario principal entendidos;
- problema y resultado esperado entendidos;
- alcance inicial y fuera de alcance definidos;
- criterio inicial de éxito;
- al menos un flujo principal candidato;
- roles o actores principales comprendidos cuando afecten el flujo;
- restricciones confirmadas separadas de referencias heredadas;
- decisiones, supuestos, propuestas y desconocidos correctamente clasificados;
- ausencia de contradicciones críticas pendientes;
- aprobación explícita del usuario a la síntesis inicial.

## 7. Crear `90 — Wiki y memoria`

Solo después de superar el gate anterior, propón una conversación separada:

```text
90 — Wiki y memoria
```

No simules `90` como una sección dentro de `00` cuando la plataforma permita conversaciones separadas.

La wiki se construye siguiendo `bootstrap-llm-wiki.md` y los principios LLM Wiki: Markdown navegable, páginas pequeñas, enlaces, Git, alta señal y separación entre fuentes, hechos, propuestas, decisiones y estado.

## 8. Conversation Spaces progresivos

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

## 9. Preparar el entorno local

Cuando el proyecto entre en desarrollo:

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

La capa conversacional puede existir antes de estas carpetas.

## 10. Primera salida hacia desarrollo

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
- decisiones de trabajo correctamente clasificadas;
- LLM Wiki mínima;
- conversaciones mínimas;
- primera tarea acotada.

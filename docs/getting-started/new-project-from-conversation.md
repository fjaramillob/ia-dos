# Iniciar un proyecto nuevo desde la capa conversacional

Este recorrido está pensado para una persona que quiere comenzar un proyecto nuevo utilizando un Project de ChatGPT, un Gem de Gemini, un Project de Claude o un entorno equivalente como punto de entrada.

La primera etapa no consiste en elegir un framework ni pedir que se construya toda la aplicación. Consiste en darle dirección al proyecto y crear una base de contexto que después pueda convertirse en trabajo de desarrollo.

## 1. Crear el Project Orchestrator

Crea un espacio dedicado al proyecto en la plataforma conversacional que utilices.

Ese espacio debe recibir como contexto:

- el repositorio IA-DOS o, cuando la plataforma no permita conectarlo completo, al menos `README.md`, `ORCHESTRATOR.md` y `docs/index.md`;
- la instrucción general del proyecto;
- cualquier fuente inicial disponible, como notas, documentos, referencias visuales o restricciones.

Cuando la plataforma permita instrucciones persistentes, puede aplicarse de forma opcional `templates/project-instructions.template.md`. Esta plantilla complementa IA-DOS, pero no reemplaza `ORCHESTRATOR.md` ni debe contener estado cambiante.

El asistente debe reconocer que IA-DOS define cómo trabajar, no qué producto construir.

## 2. Primera conversación: `00 — Dirección y definición`

La primera conversación debe centrarse en entender el proyecto.

El asistente debe ayudar a aclarar, de forma progresiva y sin convertir la conversación en un formulario rígido:

- qué problema se quiere resolver;
- para quién existe el proyecto;
- qué resultado debería producir;
- cuál es el alcance inicial;
- qué queda fuera de alcance;
- cómo se espera que opere;
- cuáles son sus flujos principales;
- cómo debería verse y sentirse;
- qué datos, integraciones o servicios podría necesitar;
- qué restricciones existen de tiempo, coste, seguridad o tecnología;
- qué decisiones todavía están abiertas;
- cómo se reconocerá que la primera versión funciona.

El asistente debe distinguir claramente hechos, preferencias, supuestos, propuestas y decisiones confirmadas.

No debe transformar preferencias tempranas en decisiones técnicas definitivas sin confirmación.

## 3. Resultado de la primera conversación

La conversación debe terminar con una primera síntesis estructurada que pueda convertirse en archivos de la wiki.

Como mínimo debe producir:

- propósito del proyecto;
- usuario principal;
- problema;
- alcance inicial;
- fuera de alcance;
- comportamiento esperado;
- dirección visual inicial;
- restricciones;
- decisiones confirmadas;
- preguntas abiertas;
- siguiente paso recomendado.

Todavía no debe afirmar que existe una aplicación, arquitectura o integración que no haya sido creada.

## 4. Crear la LLM Wiki

Después de definir el proyecto, el orquestador debe abrir o proponer:

```text
90 — Wiki y memoria
```

Esa conversación utiliza la síntesis de dirección para crear la primera LLM Wiki del proyecto.

La wiki debe separar lo que ya está decidido de lo que sigue siendo una propuesta. En un proyecto nuevo, `current-state.md` debe indicar que el producto todavía no está implementado y registrar únicamente los activos que sí existen.

Consulta [Crear la LLM Wiki](bootstrap-llm-wiki.md).

## 5. Crear Conversation Spaces de forma progresiva

No abras una taxonomía completa de conversaciones desde el primer día.

El mínimo inicial es:

```text
00 — Dirección y orquestación
90 — Wiki y memoria
```

La conversación `00` comienza como `Dirección y definición` y, después de esa etapa, pasa a operar como `Dirección y orquestación`.

Cuando comience el trabajo técnico, agrega:

```text
30 — Ejecución y desarrollo
```

Su función es preparar `Execution Tasks`, realizar handoffs hacia coding agents y revisar `Execution Reports`.

Agrega conversaciones opcionales solo cuando exista actividad recurrente, mezcla de contexto, fuentes propias, varias tareas relacionadas o necesidad de revisión especializada. Ejemplos:

```text
10 — Producto y UX
20 — Arquitectura y datos
40 — QA y seguridad
```

Un proyecto pequeño puede mantenerse solo con `00`, `30` y `90`. No abras un chat solo porque un dominio existe conceptualmente.

## 6. Relación con Codex, Antigravity u otros coding agents

No existe una relación uno a uno entre Conversation Spaces y coding agents.

La unidad de ejecución es:

```text
1 Execution Task
→ 1 ejecución acotada del coding agent
→ 1 resultado verificable
→ 1 Execution Report
```

Un Conversation Space puede originar múltiples tareas. Las sesiones del coding agent ejecutan trabajo; no conservan la memoria canónica del proyecto.

## 7. Preparar el entorno local

Cuando el proyecto vaya a entrar en desarrollo, se crea o incorpora el workspace local recomendado:

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

La capa conversacional puede existir antes que estas carpetas. La clonación local comienza cuando el usuario necesita trabajar con repositorios, archivos, agentes de desarrollo o Git.

## 8. Primera salida hacia desarrollo

El orquestador no debe pedir al coding agent que construya todo el producto de una vez.

Debe preparar una primera `Execution Task` acotada, por ejemplo:

- inicializar la aplicación con el stack ya decidido;
- crear la estructura base sin implementar funcionalidades;
- construir un primer flujo vertical verificable;
- inspeccionar y documentar una decisión técnica antes de implementarla.

La tarea debe incluir contexto mínimo, alcance, fuera de alcance, criterios de aceptación, pruebas y condiciones de detención.

## Resultado esperado

Al finalizar este recorrido deben existir:

- un Project Orchestrator contextualizado con IA-DOS;
- una definición inicial del proyecto;
- una LLM Wiki mínima;
- una separación clara entre decisiones, propuestas y preguntas abiertas;
- una estructura mínima de conversaciones;
- una primera tarea de desarrollo acotada.
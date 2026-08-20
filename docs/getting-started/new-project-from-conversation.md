# Iniciar un proyecto nuevo desde la capa conversacional

Este recorrido comienza en conversación. La preparación local aparece después, cuando una tarea necesita repositorios, archivos, Git o un coding agent.

## 1. Inicializar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md` y entrega una descripción inicial, documentos, repositorios o fuentes disponibles.

## 2. Confirmar el escenario

Clasifica el producto objetivo como nuevo. Una migración, reconstrucción o sistema anterior usado como referencia no cambia por sí solo esta clasificación.

## 3. Abrir `00 — Dirección y orquestación`

Para un producto nuevo, `00` trabaja en modo `definición inicial` y captura solo lo necesario para avanzar:

- propósito;
- usuario principal;
- problema central;
- promesa de valor;
- principios no negociables;
- prioridad o primer resultado;
- límites y riesgos relevantes.

La primera respuesta debe incluir:

1. Lo que entendí.
2. Prioridad propuesta.
3. Qué falta resolver ahora.
4. Organización de conversaciones.
5. Cómo trabajaremos.
6. Tu siguiente acción.

## 4. Organizar conversaciones bajo demanda

Usa `docs/orchestration/topic-routing-registry.md` como única lista normativa de Conversation Spaces.

`00` debe indicar si basta seguir allí o si la brecha dominante justifica abrir un único espacio especializado con contexto persistente propio.

No copies ni mantengas aquí una lista paralela de tópicos. No abras espacios como secuencia automática. Si `00` ya puede preparar una `Execution Task`, pasa directamente a ejecución.

## 5. Activar Launch Mode

Cuando el usuario indique que quiere avanzar:

1. confirma la dirección en pocas líneas;
2. identifica el siguiente resultado verificable;
3. evalúa primero si puede ejecutarse directamente;
4. si falta inspección o diseño técnico, prepara una `Planning Task` de solo lectura;
5. abre otro Conversation Space solo cuando una decisión de dominio indispensable requiera contexto persistente propio;
6. prepara una `Execution Task` tan pronto como la unidad esté definida y sea segura.

La Planning Task vuelve al mismo Cycle Owner como `Implementation Plan`. No abre por sí sola otro ciclo ni autoriza ejecución.

## 6. Preparar el entorno cuando corresponda

La instalación local no es un requisito previo del onboarding. Se recomienda cuando la siguiente tarea necesita acceso real a repositorios, archivos, Git o herramientas locales.

En ese momento, el Orchestrator puede enlazar las instrucciones aplicables:

- [Preparar el workspace local](workspace-setup.md)
- [Instalar IA-DOS](install-ia-dos.md)
- [Crear el proyecto en el workspace](create-new-project-workspace.md)
- [Crear o conectar la LLM Wiki](bootstrap-llm-wiki.md)
- [Preparar el handoff de ejecución](execution-handoff.md)

Estas guías son opciones de implementación. No impongas una topología física cuando el proyecto no la necesita.

## 7. Ejecutar y retornar

```text
Conversation Space Cycle Owner
→ Execution Task
→ Execution Cell adecuada o entorno de ejecución disponible
→ coding agent
→ cambios + verificaciones
→ Execution Report
→ mismo Cycle Owner
→ revisión e iteración
```

Una `Execution Task` no implica una conversación nueva. Si el proyecto utiliza Execution Cells y ya existe una conversación activa adecuada que continúa respondiendo bien, reutilízala.

Cada Execution Task vuelve a declarar permisos, alcance, criterios y condiciones de detención. La conversación puede persistir; la autorización no.

Exchange Protocol v0 puede utilizarse para conservar el par `TASK/REPORT` fuera del chat, pero es opcional y no cambia el contrato de ejecución.

Solo vuelve a `00` cuando exista una reorientación real: cambio de objetivo, conflicto entre dominios, expansión importante de alcance o decisión humana estratégica.

## Memoria durable

La memoria durable se construye de forma progresiva a partir de conocimiento confirmado. No copies conversaciones completas en la Wiki ni obligues al coding agent a leerla completa.

El gate específico para asegurar un bootstrap mínimo de memoria antes de depender de contexto histórico se define por separado en la guía de memoria y no debe improvisarse dentro de este recorrido.

## Resultado esperado

- dirección inicial clara;
- `00 — Dirección y orquestación` usado en modo `definición inicial`;
- organización mínima de conversaciones;
- registro canónico usado para enrutar tópicos;
- ningún espacio abierto por rutina;
- primera Planning Task o Execution Task verificable preparada;
- entorno preparado solo cuando la ejecución lo requiere;
- Execution Cell reutilizada cuando corresponda;
- Execution Report devuelto al Cycle Owner;
- memoria durable actualizada progresivamente con conocimiento confirmado.

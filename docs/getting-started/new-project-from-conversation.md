# Iniciar un proyecto nuevo desde la capa conversacional

Este recorrido comienza en conversación. La preparación local aparece después, cuando una tarea necesita repositorios, archivos, Git o un coding agent.

## 1. Inicializar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md` y entrega una descripción inicial, documentos, repositorios o fuentes disponibles.

## 2. Confirmar el escenario

Clasifica el producto objetivo como nuevo. Una migración, reconstrucción o sistema anterior usado como referencia no cambia por sí solo esta clasificación.

## 3. Abrir `00 — Dirección y definición`

`00` captura solo lo necesario para avanzar:

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

`00` debe indicar si basta seguir allí o si existe una brecha que justifique abrir un único espacio especializado:

- `10 — Producto y UX` para comportamiento, flujo o experiencia;
- `20 — Arquitectura y stack` para decisiones técnicas o lectura de una auditoría;
- `30 — Ejecución y desarrollo` solo cuando una tarea compleja necesita preparación adicional;
- `90 — Wiki y memoria` para síntesis, contradicciones o mantenimiento documental complejo.

No abras estos espacios como secuencia automática. Si `00` ya puede preparar una `Execution Task`, pasa directamente a ejecución.

## 5. Activar Launch Mode

Cuando el usuario indique que quiere avanzar:

1. confirma la dirección en pocas líneas;
2. identifica el siguiente resultado verificable;
3. evalúa si existe claridad suficiente para ejecutar;
4. abre como máximo un Conversation Space si falta una definición indispensable;
5. prepara una `Execution Task` tan pronto como la tarea esté acotada.

## 6. Preparar el entorno local cuando corresponda

La instalación local no es un requisito previo del onboarding. Se recomienda cuando la siguiente tarea necesita acceso real a repositorios, archivos, Git o herramientas locales.

En ese momento, el Orchestrator debe enlazar o incluir las instrucciones aplicables:

- [Preparar el workspace local](workspace-setup.md)
- [Instalar IA-DOS](install-ia-dos.md)
- [Crear el proyecto en el workspace](create-new-project-workspace.md)
- [Crear o conectar la LLM Wiki](bootstrap-llm-wiki.md)
- [Preparar el handoff de ejecución](execution-handoff.md)

## 7. Ejecutar y retornar

```text
Conversation Space de origen
→ Execution Task
→ coding agent
→ cambios y verificaciones
→ Execution Report
→ regreso al espacio de origen
→ revisión e iteración
```

Solo vuelve a `00` cuando exista una reorientación real: cambio de objetivo, conflicto entre dominios, expansión importante de alcance o decisión humana estratégica.

## Resultado esperado

- dirección inicial clara;
- organización mínima de conversaciones;
- ningún espacio abierto por rutina;
- primera tarea verificable preparada;
- entorno local sugerido solo cuando la ejecución lo requiere;
- Execution Report devuelto al espacio que originó la tarea;
- Wiki actualizada progresivamente con conocimiento confirmado.

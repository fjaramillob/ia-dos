# Adoptar un proyecto existente desde la capa conversacional

Este recorrido comienza en conversación y pasa al entorno técnico cuando hace falta inspeccionar o modificar artefactos reales.

## 1. Inicializar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md` y entrega las fuentes disponibles: repositorio, Wiki, documentación, reportes, enlaces y restricciones.

## 2. Confirmar el escenario

Clasifica el producto objetivo como existente cuando el propio producto tiene evidencia de implementación, usuarios, despliegue, infraestructura, integraciones o documentación técnica vigente.

Una migración, reconstrucción o producto sucesor es un atributo, no un tercer escenario.

## 3. Abrir `00 — Dirección y orquestación`

Para un producto existente, `00` trabaja en modo `descubrimiento y adopción` y debe comprender solo lo necesario para orientar la siguiente unidad:

- qué producto existe;
- qué está implementado, parcial, planificado, deprecado o desconocido;
- qué fuentes y repositorios participan;
- qué decisiones siguen vigentes;
- qué problemas o riesgos son conocidos;
- cuál es la prioridad actual.

No describas como real algo que no tenga evidencia.

## 4. Organizar conversaciones bajo demanda

Usa `docs/orchestration/topic-routing-registry.md` como única lista normativa de Conversation Spaces.

`00` debe indicar si basta continuar allí o si la brecha dominante requiere un espacio especializado con contexto persistente propio.

No mantengas aquí una lista paralela de tópicos. No abras `90`, `30` ni ningún otro espacio por rutina. Si el espacio actual ya puede preparar una `Execution Task`, pasa directamente a ejecución.

## 5. Obtener evidencia cuando falte

Cuando el asistente conversacional no tenga acceso suficiente al estado real, prepara una `Planning Task` o un `Environment Preflight` según la incertidumbre:

- solo lectura;
- fuentes, repositorios o entornos explícitos;
- verificaciones no destructivas;
- evidencia verificable;
- ninguna modificación remota sin autorización.

El resultado vuelve al mismo Cycle Owner. No abras otro Conversation Space solo para ejecutar la inspección técnica.

## 6. Preparar el entorno cuando corresponda

La instalación local no es requisito previo del onboarding. Se recomienda cuando la siguiente tarea necesita acceso real a repositorios, archivos, Git o herramientas locales.

En ese momento, usa según corresponda:

- [Preparar el workspace local](workspace-setup.md)
- [Instalar IA-DOS](install-ia-dos.md)
- [Incorporar el proyecto existente](incorporate-existing-project-workspace.md)
- [Crear o revisar la LLM Wiki](bootstrap-llm-wiki.md)
- [Preparar el handoff de ejecución](execution-handoff.md)

No muevas, renombres ni reorganices un proyecto existente solo para cumplir una estructura recomendada.

## 7. Ejecutar y retornar

```text
Conversation Space Cycle Owner
→ Execution Task
→ Execution Cell adecuada o entorno disponible
→ coding agent
→ cambios + verificaciones
→ Execution Report
→ mismo Cycle Owner
→ revisión e iteración
```

Una Execution Task no obliga a crear una conversación nueva del coding agent. Cuando exista una Execution Cell adecuada y su conversación activa continúe respondiendo correctamente, reutilízala.

Cada tarea vuelve a declarar alcance y permisos. La continuidad conversacional no hereda autorizaciones anteriores.

Exchange Protocol v0 puede conservar `TASK/REPORT` fuera de la conversación, pero es opcional y no sustituye backlog, memoria durable ni implementación.

Solo vuelve a `00` cuando aparezca una reorientación real.

## Primera unidad recomendada

Comienza con un resultado de bajo riesgo y verificable, por ejemplo:

- inspeccionar una incertidumbre técnica concreta;
- documentar un flujo existente;
- corregir un bug acotado;
- añadir una prueba;
- actualizar una funcionalidad pequeña;
- verificar una integración.

No conviertas la adopción en una auditoría integral antes de poder avanzar.

## Memoria durable

La Wiki o mecanismo de memoria adoptado debe distinguir conocimiento vigente de historia operacional. No copies conversaciones completas ni trates un Execution Report como estado oficial sin revisión.

El gate específico de bootstrap mínimo de memoria se define separadamente y no debe improvisarse dentro de esta fase de onboarding.

## Resultado esperado

- producto clasificado con evidencia;
- `00 — Dirección y orquestación` usado en modo `descubrimiento y adopción`;
- estado real comprendido sin inventar historia;
- organización mínima de conversaciones;
- registro canónico usado para enrutar tópicos;
- entorno preparado solo cuando hace falta;
- primera Planning Task, Preflight o Execution Task acotada;
- Execution Cell reutilizada cuando corresponda;
- evidencia devuelta al Cycle Owner;
- memoria durable creada o actualizada progresivamente.

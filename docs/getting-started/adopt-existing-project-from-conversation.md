# Adoptar un proyecto existente desde la capa conversacional

Este recorrido comienza en conversación y pasa al entorno local cuando hace falta inspeccionar o modificar artefactos reales.

## 1. Inicializar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md` y entrega las fuentes disponibles: repositorio, Wiki, documentación, reportes, enlaces y restricciones.

## 2. Confirmar el escenario

Clasifica el producto objetivo como existente cuando el propio producto tiene evidencia de implementación, usuarios, despliegue, infraestructura, integraciones o documentación técnica vigente.

Una migración, reconstrucción o producto sucesor es un atributo, no un tercer escenario.

## 3. Abrir `00 — Descubrimiento y adopción`

`00` debe comprender:

- qué producto existe;
- qué está implementado, parcial, planificado, deprecado o desconocido;
- qué fuentes y repositorios participan;
- qué decisiones siguen vigentes;
- qué problemas o riesgos son conocidos;
- cuál es la prioridad actual.

No describas como real algo que no tenga evidencia.

## 4. Organizar conversaciones bajo demanda

`00` debe indicar si basta continuar allí o si una brecha requiere un único espacio especializado:

- `10 — Producto y UX` para comportamiento o experiencia;
- `20 — Arquitectura y stack` para una auditoría o decisión técnica;
- `30 — Ejecución y desarrollo` solo si una tarea compleja necesita preparación adicional;
- `90 — Wiki y memoria` para síntesis, contradicciones o mantenimiento documental complejo.

No abras `90` automáticamente porque exista documentación dispersa ni abras `30` por rutina. Si el espacio actual ya puede preparar una `Execution Task`, pasa directamente a ejecución.

## 5. Usar inspección en modo lectura cuando falte evidencia

Cuando el asistente conversacional no tenga acceso suficiente al estado real, prepara una tarea de inspección para el coding agent:

- solo lectura;
- repositorios y rutas explícitos;
- verificaciones no destructivas;
- formato de evidencia;
- ninguna modificación remota sin autorización.

El reporte vuelve al espacio que originó la inspección.

## 6. Preparar el entorno local cuando corresponda

La instalación local no es requisito previo del onboarding. Se recomienda cuando la siguiente tarea necesita acceso real a repositorios, archivos, Git o herramientas locales.

En ese momento, usa:

- [Preparar el workspace local](workspace-setup.md)
- [Instalar IA-DOS](install-ia-dos.md)
- [Incorporar el proyecto existente](incorporate-existing-project-workspace.md)
- [Crear o revisar la LLM Wiki](bootstrap-llm-wiki.md)
- [Preparar el handoff de ejecución](execution-handoff.md)

No muevas, renombres ni reorganices un proyecto existente solo para cumplir una estructura recomendada.

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

Solo vuelve a `00` cuando aparezca una reorientación real.

## Primera tarea recomendada

Comienza con un resultado de bajo riesgo y verificable, por ejemplo:

- inspeccionar arquitectura actual;
- documentar un flujo existente;
- corregir un bug acotado;
- añadir una prueba;
- actualizar una funcionalidad pequeña;
- verificar una integración.

## Resultado esperado

- producto clasificado con evidencia;
- estado real comprendido sin inventar historia;
- organización mínima de conversaciones;
- entorno local preparado solo cuando hace falta;
- primera tarea acotada;
- evidencia devuelta al espacio de origen;
- Wiki creada o actualizada progresivamente.

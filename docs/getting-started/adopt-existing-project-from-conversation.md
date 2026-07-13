# Adoptar un proyecto existente desde la capa conversacional

Este recorrido sirve para adoptar un producto objetivo que ya tiene implementación, documentación, usuarios, infraestructura o integraciones.

## 1. Configurar el Project Orchestrator

Utiliza `prompts/getting-started/initialize-project-orchestrator.md`.

Entrega como conocimiento:

1. `bundles/ia-dos-project-orchestrator-pack.md` cuando la plataforma no pueda navegar GitHub;
2. repositorio de aplicación o un reporte de inspección;
3. documentación existente, wiki, enlaces, reportes y restricciones.

El asistente debe leer primero las fuentes y evitar preguntas repetidas.

## 2. Confirmar que el producto objetivo es existente

Clasifica el producto objetivo, no los sistemas anteriores o relacionados.

Existe evidencia suficiente cuando el producto objetivo mismo tiene uno o más de estos elementos:

- código;
- despliegue;
- usuarios;
- infraestructura;
- integraciones activas;
- documentación técnica vigente.

Una migración, reconstrucción o producto sucesor no constituye un tercer escenario. Es un atributo de la iniciativa.

## 3. Primera conversación: `00 — Descubrimiento y adopción`

Determina:

- qué producto existe;
- para quién funciona;
- qué está implementado, parcial, planificado, deprecado o desconocido;
- qué documentación existe;
- qué decisiones siguen vigentes;
- qué repositorios, servicios e integraciones participan;
- qué problemas o riesgos son conocidos;
- cuál es la prioridad actual.

Regla:

> No describas como real algo que no haya sido confirmado por una fuente, el usuario o una inspección del repositorio.

## 4. Verificar la LLM Wiki

### Existe una wiki usable

Revisa si está versionada, tiene punto de entrada, representa el estado actual, distingue planes de implementación, contiene decisiones y fuentes, y puede ser utilizada por personas y agentes.

No la reemplaces automáticamente.

### Existe documentación dispersa

Identifica qué conservar como fuente y qué sintetizar. No copies todo sin criterio.

### No existe wiki

Propón una conversación separada:

```text
90 — Wiki y memoria
```

No simules `90` como una sección dentro de `00` cuando la plataforma permita conversaciones separadas.

Construye la wiki desde evidencia siguiendo `bootstrap-llm-wiki.md` y los principios LLM Wiki: Markdown navegable, páginas pequeñas, enlaces, Git y alta señal.

## 5. Construir memoria sin inventar historia

Usa:

- inspección del repositorio en modo lectura;
- README, configuración, dependencias y estructura;
- documentación existente;
- issues y pull requests relevantes;
- conversación con la persona responsable;
- dudas y contradicciones explícitas.

Clasifica hallazgos como:

```text
Implementado
Parcialmente implementado
Planificado
Deprecado
Desconocido
```

## 6. Conversation Spaces progresivos

Comienza con:

```text
00 — Dirección y orquestación
90 — Wiki y memoria
```

Cuando empiece el trabajo técnico:

```text
30 — Ejecución y desarrollo
```

Agrega producto, arquitectura, QA, operaciones, comercial o cumplimiento solo cuando exista actividad recurrente o mezcla real de contexto.

## 7. Conectar conversación, wiki y aplicación

```text
IA-DOS
    define cómo trabajar

Project Orchestrator
    dirige y convierte conversaciones en trabajo

LLM Wiki
    conserva contexto, decisiones y estado

Repositorio de aplicación
    conserva la implementación
```

Cuando no haya acceso al repositorio, solicita a un coding agent una inspección en modo lectura y un reporte estructurado.

## 8. Relación con coding agents

```text
1 Execution Task
→ 1 ejecución acotada
→ 1 resultado verificable
→ 1 Execution Report
```

Las sesiones del coding agent no son memoria durable.

## 9. Primera tarea después de la adopción

Valida el flujo con una tarea de bajo riesgo:

- documentar arquitectura actual;
- corregir un bug acotado;
- añadir una prueba;
- actualizar una funcionalidad pequeña;
- verificar una integración.

## Resultado esperado

- Project Orchestrator dedicado;
- producto objetivo clasificado con evidencia;
- comprensión del estado real;
- wiki creada o revisada;
- contradicciones registradas;
- conversaciones mínimas;
- primera tarea acotada.
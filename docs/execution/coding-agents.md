# Coding agents

Un coding agent es la herramienta que materializa cambios sobre archivos, repositorios y entornos de desarrollo dentro de límites explícitos.

Ejemplos incluyen Codex, Claude Code, Antigravity y agentes integrados en un IDE.

## Rol

El coding agent convierte una `Execution Task` autorizada en un resultado verificable.

Su trabajo puede incluir:

- inspeccionar repositorios y archivos;
- crear o modificar código;
- crear o actualizar documentación;
- construir o mantener una LLM Wiki;
- ejecutar comandos y pruebas;
- trabajar con branches, commits y pull requests;
- entregar un `Execution Report` con evidencia.

## Frontera con el Project Orchestrator

```text
Project Orchestrator
    comprende, decide, delimita y revisa

Coding agent
    inspecciona, materializa, prueba y reporta
```

El Orchestrator selecciona el contexto y define la tarea. El coding agent realiza la modificación física.

Un coding agent no debe asumir autoridad para cambiar propósito, prioridades, arquitectura, alcance, costes, seguridad o producción cuando la tarea no lo autoriza.

## Entrada mínima

Antes de ejecutar, debe recibir:

- objetivo;
- contexto durable estrictamente necesario;
- alcance y fuera de alcance cuando aplique;
- archivos o repositorios autorizados cuando aplique;
- guardrails;
- criterios de aceptación;
- pruebas esperadas cuando correspondan;
- condiciones de detención cuando sean relevantes;
- formato del reporte final.

No debe recibir automáticamente todo IA-DOS, toda la wiki o todos los repositorios del workspace.

Una tarea puede distinguir entre:

- `Contexto durable necesario`: extracto mínimo incluido en la tarea;
- `Referencias Wiki`: trazabilidad, sin obligación automática de lectura;
- `Lectura requerida`: archivos concretos que sí deben consumirse antes de ejecutar.

## Execution Cells

Una conversación del coding agent puede representar una `Execution Cell`: un contexto durable de ejecución definido por proyecto.

La célula no representa una tarea ni una profesión. Por ejemplo, una célula `App` puede resolver trabajo de frontend, backend, datos, tests y despliegue si todos forman parte del mismo contexto de producto.

Mantén una sola conversación activa por célula mientras siga respondiendo bien. Renueva la conversación únicamente cuando exista evidencia de degradación o contaminación de contexto.

Reutilizar una conversación no acumula permisos. Cada nueva `Execution Task` vuelve a declarar su autoridad y el coding agent no inicia por sí mismo la siguiente unidad.

Consulta [Execution Cells y Exchange Protocol v0](execution-cells-and-exchange.md).

## Conducta durante la ejecución

El coding agent debe:

1. inspeccionar antes de modificar;
2. confirmar que está en el repositorio y branch correctos cuando corresponda;
3. leer solo el contexto necesario;
4. preservar el comportamiento fuera de alcance;
5. evitar dependencias o refactors no solicitados;
6. detenerse ante contradicciones, falta de acceso o decisiones importantes no resueltas;
7. ejecutar las verificaciones aplicables;
8. revisar el diff completo;
9. reportar cambios, pruebas, riesgos y pendientes.

## Tipos de materialización

IA-DOS reconoce, como mínimo:

- `Application Execution Task`: modifica la implementación;
- `Documentation Execution Task`: modifica documentación técnica o pública;
- `Wiki Update Task`: modifica memoria durable del proyecto.

La naturaleza documental de una tarea no elimina la necesidad de alcance, autorización, diff y evidencia.

## Ejecución de una `Wiki Update Task`

Cuando la tarea afecta la LLM Wiki, el coding agent no decide qué conocimiento debe convertirse en memoria durable. Esa definición proviene del Project Orchestrator y, cuando existe, de `90 — Wiki y memoria`.

El coding agent debe:

1. leer la `Wiki Update Task` y las fuentes autorizadas;
2. inspeccionar la estructura y el estado real de la wiki;
3. modificar únicamente las páginas permitidas;
4. preservar contenido vigente que no fue autorizado a reemplazar;
5. distinguir hechos, decisiones, hipótesis, propuestas y desconocidos;
6. no convertir una hipótesis en hecho ni una propuesta en decisión vigente;
7. validar Markdown, YAML, enlaces, navegación y referencias cuando corresponda;
8. comprobar que no se incorporaron secretos ni datos sensibles;
9. revisar el diff completo;
10. devolver un `Execution Report` y el pull request cuando esté autorizado.

El flujo detallado se encuentra en [Actualizar la LLM Wiki](updating-the-llm-wiki.md).

Cuando la Wiki se consume también desde Obsidian, conserva Markdown portable y evita depender de funciones propietarias para comprender la fuente canónica. Consulta [Memoria durable portable y consumo desde Obsidian](../foundations/durable-memory-and-obsidian.md).

## Evidencia esperada

Una ejecución no se considera verificada solo porque el agente afirma que terminó.

El `Execution Report` debe incluir, según corresponda:

- archivos creados, modificados o eliminados;
- resumen del diff;
- comandos ejecutados;
- resultados de lint, typecheck, build y pruebas;
- revisión visual o manual;
- errores encontrados;
- riesgos y supuestos restantes;
- enlace o referencia al pull request.

En Exchange v0, el reporte puede además señalar `Conocimiento potencialmente durable` sin modificar la Wiki ni declararlo como hecho oficial.

## Git y pull requests

Cuando la tarea lo autorice, el coding agent debe trabajar en una branch dedicada, producir commits intencionales y preparar un pull request revisable.

No debe fusionar el cambio salvo autorización explícita.

## Memoria

Las sesiones del coding agent no son memoria durable.

Después de la revisión, el aprendizaje confirmado debe regresar a la LLM Wiki, ADR, issue, documentación o fuente de verdad correspondiente mediante una tarea autorizada.

Cuando un proyecto adopta Exchange, `TASK` y `REPORT` pueden conservarse como historial operacional fuera de la conversación. Exchange no sustituye la memoria durable ni la implementación.

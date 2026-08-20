# Coding agents

Un coding agent es la herramienta que materializa cambios sobre archivos, repositorios y entornos de desarrollo dentro de límites explícitos.

Ejemplos incluyen Codex, Claude Code, Antigravity y agentes integrados en un IDE.

## Rol

El coding agent convierte una `Execution Task` autorizada en un resultado verificable. También puede actuar como `Coding Agent — Planning` cuando recibe una `Planning Task` de solo lectura.

Su trabajo puede incluir:

- inspeccionar repositorios y archivos;
- crear o modificar código;
- crear o actualizar documentación;
- construir o mantener memoria durable Markdown;
- ejecutar comandos y pruebas;
- trabajar con branches, commits y pull requests cuando estén autorizados;
- entregar un `Implementation Plan` o `Execution Report` según el rol recibido.

## Frontera con el Project Orchestrator

```text
Project Orchestrator
    comprende, decide, delimita y revisa

Coding agent
    inspecciona, planifica o materializa, verifica y reporta
```

El Orchestrator selecciona el contexto y define la tarea. El coding agent trabaja sobre los recursos reales dentro del contrato recibido.

Un coding agent no debe asumir autoridad para cambiar propósito, prioridades, arquitectura, alcance, costes, seguridad o producción cuando la tarea no lo autoriza.

## Entrada mínima de ejecución

Antes de ejecutar, debe recibir:

- objetivo;
- contexto durable estrictamente necesario;
- alcance y fuera de alcance;
- autoridad y acceso de los recursos relevantes;
- permisos y acciones externas autorizadas;
- guardrails;
- criterios de aceptación;
- verificaciones esperadas;
- condiciones de detención;
- destino y formato del reporte final.

No debe recibir automáticamente todo IA-DOS, toda la Wiki o todos los repositorios del workspace.

Una tarea puede distinguir entre:

- `Contexto durable necesario`: extracto mínimo incluido en la tarea;
- `Referencias Wiki`: trazabilidad, sin obligación automática de lectura;
- `Lectura requerida`: archivos concretos que sí deben consumirse antes de actuar.

Cuando la información necesaria sólo vive en conversaciones y debe reutilizarse, corresponde al Project Orchestrator evaluar el `Memory Bootstrap Gate`; el coding agent no reconstruye por defecto el historial conversacional.

## Execution Cells

Una conversación del coding agent puede representar una `Execution Cell`: un contexto durable de ejecución definido por proyecto.

La célula no representa una tarea ni una profesión. Por ejemplo, una célula `App` puede resolver trabajo de frontend, backend, datos, tests y despliegue si todos forman parte del mismo contexto operacional.

Mantén una sola conversación activa por célula mientras siga respondiendo bien. Renueva la conversación únicamente cuando exista evidencia de degradación o contaminación de contexto.

Reutilizar una conversación no acumula permisos. Cada nueva `Execution Task` vuelve a declarar su autoridad y el coding agent no inicia por sí mismo la siguiente unidad.

Consulta [Execution Cells y Exchange Protocol v0](execution-cells-and-exchange.md).

## Conducta durante la ejecución

El coding agent debe:

1. inspeccionar antes de modificar;
2. confirmar que está en el recurso y branch o modo correctos cuando corresponda;
3. leer sólo el contexto requerido;
4. preservar el comportamiento fuera de alcance;
5. evitar dependencias o refactors no solicitados;
6. detenerse ante contradicciones, falta de acceso o decisiones importantes no resueltas;
7. ejecutar las verificaciones aplicables;
8. revisar el diff completo;
9. reportar cambios, pruebas, riesgos y pendientes.

## Perfiles de materialización

Una `Execution Task` puede especializar su propósito sin convertirse en un tipo de artefacto distinto. Por ejemplo:

- aplicación: modifica la implementación;
- documentación: modifica documentación técnica o pública;
- `Wiki Update Task`: perfil documental para modificar memoria durable Markdown.

La naturaleza documental de una tarea no elimina la necesidad de alcance, autoridad, permisos, diff y evidencia.

## Ejecución de una `Wiki Update Task`

Cuando una tarea afecta memoria durable, el coding agent no decide unilateralmente qué conocimiento debe convertirse en estado oficial. Esa definición proviene del Cycle Owner y, cuando aporta, de `90 — Wiki y memoria`.

El coding agent debe:

1. leer el perfil `Wiki Update Task` y las fuentes autorizadas;
2. inspeccionar el home real y sólo las páginas declaradas como lectura requerida;
3. modificar únicamente las rutas permitidas;
4. preservar contenido vigente que no fue autorizado a reemplazar;
5. distinguir implementado, decidido/no implementado, pendiente, fuera de alcance y desconocido;
6. no convertir una propuesta en hecho ni una decisión aceptada en implementación;
7. validar Markdown, enlaces relativos, navegación y YAML cuando corresponda;
8. mantener la memoria comprensible fuera de Obsidian y no depender de plugins o wikilinks para semántica crítica;
9. comprobar que no se incorporaron secretos ni datos sensibles;
10. revisar el diff completo;
11. devolver un `Execution Report` y la referencia remota sólo cuando esa acción haya sido autorizada.

El flujo detallado se encuentra en [Actualizar la memoria durable](updating-the-llm-wiki.md).

## Evidencia esperada

Una ejecución no se considera verificada sólo porque el agente afirma que terminó.

El `Execution Report` debe incluir, según corresponda:

- archivos creados, modificados o eliminados;
- resumen del diff;
- comandos ejecutados;
- resultados de lint, typecheck, build y pruebas;
- revisión visual o manual;
- errores encontrados;
- riesgos y supuestos restantes;
- enlace o referencia al pull request cuando exista.

En Exchange v0, el reporte puede además señalar `Conocimiento potencialmente durable` sin modificar la memoria ni declararlo como hecho oficial.

## Git y pull requests

Branch, commit, push, pull request y merge son capacidades separadas.

El coding agent sólo debe realizar cada una cuando la tarea la autorice explícitamente. No fusiona un cambio por cuenta propia salvo autorización específica.

## Memoria

Las sesiones del coding agent no son memoria durable.

Después de la revisión, el aprendizaje confirmado que deba reutilizarse regresa a la memoria durable, ADR, issue, documentación o fuente de verdad correspondiente mediante una tarea autorizada.

Cuando un proyecto adopta Exchange, `TASK` y `REPORT` pueden conservarse como historial operacional fuera de la conversación. Exchange no sustituye la memoria durable ni la implementación.

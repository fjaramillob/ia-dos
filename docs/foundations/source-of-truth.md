# Fuentes de verdad

IA-DOS evita mantener la misma información manualmente en varios lugares.

Cada tipo de información debe tener una ubicación principal.

| Información | Fuente de verdad recomendada |
|---|---|
| Propósito, usuarios y alcance | Wiki del proyecto |
| Estado actual | Wiki del proyecto |
| Arquitectura vigente | Wiki del proyecto |
| Decisión durable | Registro de decisión en la wiki |
| Estructura de conversaciones | Configuración documentada del Project, Gem o asistente |
| Instrucciones del orquestador | Archivo o prompt de orquestación adoptado por el proyecto |
| Instrucciones para coding agents | `AGENTS.md` |
| Trabajo pendiente | GitHub Issue o mecanismo elegido por el proyecto |
| Alcance de un cambio | `Execution Task` |
| Implementación | Repositorio de aplicación |
| Revisión y evidencia | Pull request o reporte de ejecución |
| Estándar común | Repositorio IA-DOS |

## Conversaciones

Las conversaciones sirven para explorar, coordinar y preparar trabajo.

No son una fuente de verdad durable.

Cuando una conversación produce una decisión, una nueva restricción, un cambio de alcance o información que debe conservarse, el resultado debe registrarse en la fuente canónica correspondiente.

## Regla

Los documentos pueden enlazarse entre sí, pero no deben copiarse completos sin una razón clara.

Cuando dos fuentes se contradicen, debe identificarse cuál es canónica y corregirse la otra.

El orquestador debe ayudar a detectar estas contradicciones y proponer dónde registrar el resultado.
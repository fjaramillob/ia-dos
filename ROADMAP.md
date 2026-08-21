# Roadmap

IA-DOS evoluciona en incrementos pequeños, revisables y validados mediante proyectos reales.

El roadmap distingue entre contratos ya consolidados y capacidades que todavía necesitan evidencia de uso antes de estabilizarse.

## Convención de memoria

IA-DOS mantiene dos niveles de vocabulario complementarios:

```text
memoria durable
= concepto funcional

LLM Wiki
= materialización durable, portable y navegable
  de esa memoria para humanos y agentes
```

`Memoria durable` describe la responsabilidad: conservar conocimiento vigente y reutilizable fuera de conversaciones efímeras.

`LLM Wiki` es el término propio de IA-DOS para la base de conocimiento del proyecto cuando esa memoria se materializa como documentación estructurada, normalmente Markdown versionable y portable entre GitHub, Obsidian, editores y agentes.

Una LLM Wiki no es obligatoria para toda tarea ni exige un repositorio separado. El `Memory Bootstrap Gate` determina cuándo hace falta persistir conocimiento antes de continuar.

---

## `v0.1.0-alpha.1` — Foundation

**Estado: COMPLETADO**

Fundamentos iniciales del método:

- propósito, alcance y público objetivo;
- `Project Orchestrator` y capa de orquestación conversacional;
- `Conversation Spaces` como dominios de gobierno;
- separación entre planificación y ejecución;
- tipado básico de artefactos;
- autoridad de fuentes y entornos;
- guardrails y verificación basada en evidencia;
- onboarding de proyecto nuevo y existente;
- starter templates y documentación canónica.

Este milestone estableció el lenguaje base de IA-DOS, pero varios contratos fueron refinados posteriormente mediante uso real.

---

## `v0.1.0-alpha.2` — Operational consolidation

**Estado: COMPLETADO**

Consolidación ejecutada durante las Fases 1–6:

- contrato semántico único de `Execution Task`;
- `Execution Report` definido como evidencia de ejecución bajo revisión del Cycle Owner;
- `Execution Cells` para continuidad operacional sin abrir una conversación por tarea;
- autorizaciones no acumulativas entre tareas;
- `Memory Bootstrap Gate`;
- contexto durable selectivo en vez de releer la memoria completa;
- LLM Wiki mínima, portable y compatible con Obsidian;
- separación entre LLM Wiki, Exchange, implementación y conversaciones;
- Exchange reducido a pasarela pasiva opcional de archivos `.md`;
- Task ID asignado por el Conversation Agent;
- `Environment Preflight` y `Execution Resume` con fronteras explícitas;
- Current Offline Pack sincronizado con los contratos canónicos;
- validación end-to-end de los principales recorridos de onboarding y continuidad.

Invariantes consolidados:

```text
Conversation Space = gobierno y decisión
Execution Cell     = continuidad de ejecución
Execution Task     = contrato de una unidad
Execution Report   = evidencia de ejecución
LLM Wiki           = memoria durable materializada
Repository         = implementación
Exchange           = pasarela pasiva de archivos
```

---

## `v0.1.0-alpha.3` — Real-project adoption

**Estado: SIGUIENTE**

Objetivo: dejar que el método siga evolucionando a partir de uso real, no de arquitectura anticipada.

### Prioridades

- aplicar la versión consolidada de IA-DOS en proyectos activos;
- validar el modelo de `Execution Cell` durante múltiples tareas sucesivas;
- comprobar que una conversación nueva pueda rehidratarse desde LLM Wiki + estado técnico + Execution Task o contrato operativo actual + delta vigente;
- medir cuánto contexto durable necesita realmente una `Execution Task`;
- validar Exchange manual como pasarela sin convertirlo en workflow o backlog;
- detectar fricción real de onboarding antes de introducir nuevas abstracciones;
- revisar la política de conversaciones de Planning sólo si el uso demuestra una necesidad concreta.

### LLM Wiki

Profundizar el patrón de LLM Wiki sin volverlo ceremonial:

- mejorar navegación y descubrimiento de conocimiento vigente;
- validar estructura mínima en proyectos pequeños y medianos;
- mantener Markdown estándar como formato canónico;
- conservar compatibilidad natural con Obsidian;
- definir mejores patrones para estado actual, decisiones y fuentes;
- comprobar cuándo conviene separar páginas por producto, arquitectura u operación;
- evitar copiar TASK/REPORT, logs o transcripciones dentro de la memoria durable;
- documentar patrones de migración desde documentación existente hacia una LLM Wiki IA-DOS.

Criterio de avance: estas mejoras deben surgir de necesidades observadas en proyectos reales y no de completar una estructura teórica.

---

## `v0.1.0-alpha.4` — Portability and adoption quality

**Estado: PLANIFICADO**

Objetivo: hacer que IA-DOS sea fácil de adoptar, transportar y mantener sin perder equivalencia entre contratos.

- validar onboarding con distintos asistentes y coding agents;
- comprobar comportamiento con y sin acceso al repositorio IA-DOS;
- mantener sincronizado el Current Offline Pack;
- crear ejemplos sintéticos completos de adopción;
- documentar actualización de una versión de IA-DOS a otra;
- mejorar detección de documentación histórica o contradictoria;
- definir checks livianos de coherencia entre Orchestrator, templates, onboarding y offline pack;
- mejorar instrucciones para proyectos que ya poseen documentación propia y no quieren reorganizarla.

No se introducirán herramientas obligatorias sólo para automatizar validaciones que todavía pueden resolverse claramente mediante contratos y revisión.

---

## `v0.1.0-beta.1` — Multi-project validation

**Estado: FUTURO**

Objetivo: validar que IA-DOS funcione de forma consistente más allá del proyecto que originó cada decisión.

Antes de beta se espera comprobar el método en varios perfiles de proyecto, por ejemplo:

- producto nuevo construido desde cero;
- aplicación existente con historia técnica importante;
- proyecto con LLM Wiki madura;
- proyecto sin Wiki inicial;
- proyecto con múltiples Execution Cells justificadas;
- proyecto operado con distintos coding agents.

La beta debe demostrar que los contratos sobreviven al cambio de proyecto y herramienta sin depender de conocimiento implícito del creador de IA-DOS.

---

## Hacia `v1.0`

`v1.0` requiere estabilidad operacional, no cantidad de features.

Antes de declararla estable, IA-DOS debe tener:

- contratos principales sin contradicciones conocidas;
- onboarding convergente y reproducible;
- LLM Wiki suficientemente validada como patrón de memoria durable;
- Execution Cells validadas en uso prolongado;
- política clara de compatibilidad y migración entre versiones;
- distribución online/offline equivalente;
- ejemplos suficientes para adoptar el método sin reconstruir su historia;
- evidencia de uso en proyectos diferentes.

---

## Deliberadamente abierto

La política universal de persistencia o renovación de conversaciones de `Coding Agent — Planning` permanece abierta.

No se resolverá por analogía con Execution Cells. Sólo se incorporará al método cuando exista evidencia de que una política explícita mejora continuidad, claridad o coste de contexto.

---

## Fuera del roadmap actual

No son prioridad de la etapa alpha:

- agentes autónomos propios de IA-DOS;
- ejecución automática al detectar archivos en Exchange;
- watchers, polling o triggers sobre Exchange;
- `REGISTRY.md`, contadores centrales o coordinación automática de Task IDs;
- dashboards operativos de IA-DOS;
- CLI;
- sincronización automática con Google Drive u otros proveedores;
- RAG o retrieval automático sobre toda la LLM Wiki;
- orquestación multiagente autónoma;
- automatización compleja que reemplace decisiones del Conversation Agent o Cycle Owner.

Estas capacidades pueden evaluarse en el futuro si resuelven problemas observados. No son requisitos para que IA-DOS funcione correctamente.
# Propósito y alcance

## Propósito

IA-DOS es un framework operativo abierto para proyectos de software desarrollados con asistencia de inteligencia artificial.

Su función es coordinar:

- la dirección humana del proyecto;
- la orquestación conversacional;
- el razonamiento especializado por dominio;
- la memoria durable;
- la delimitación del trabajo;
- la planificación técnica cuando hace falta;
- la comprobación de readiness cuando es indispensable;
- la materialización mediante coding agents;
- la verificación basada en evidencia;
- el aprendizaje que regresa a las fuentes de verdad cuando corresponde.

IA-DOS busca que una persona pueda utilizar distintos asistentes y agentes sin depender de conversaciones aisladas, crear fuentes de verdad paralelas ni perder el control del proyecto.

## Problema que aborda

Los asistentes conversacionales y coding agents pueden ayudar con rapidez, pero no conocen por sí solos:

- el propósito completo del proyecto;
- qué conversación debe tratar cada tema;
- qué decisiones siguen vigentes;
- dónde está la fuente de verdad;
- qué contexto durable necesita una tarea;
- qué zonas puede modificar un agente;
- qué riesgos y permisos aplican;
- qué información está implementada, decidida, pendiente o desconocida;
- qué evidencia se necesita para considerar una tarea terminada.

Sin una estructura común, el desarrollo puede acumular cambios fuera de alcance, conversaciones contradictorias, documentación desactualizada y consumo excesivo de contexto.

## Separación de funciones

IA-DOS mantiene fronteras visibles entre:

```text
persona responsable
→ dirección y aprobación humana

Conversation Space / Cycle Owner
→ gobierno conversacional dentro de autoridad delegada

Coding Agent — Planning
→ inspección y propuesta en solo lectura

Coding Agent — Execution
→ materialización autorizada

Execution Report
→ evidencia

LLM Wiki
→ memoria durable materializada, cuando el proyecto la adopta

Repository
→ implementación real

Exchange
→ pasarela pasiva opcional de archivos
```

Esta separación evita confundir conversación, decisión, implementación, evidencia y memoria.

## Capa de orquestación

IA-DOS reconoce una capa de trabajo anterior y posterior a la ejecución técnica.

Puede vivir en ChatGPT, Gemini, Claude u otro entorno conversacional equivalente.

Su función es:

- comprender sólo el contexto necesario;
- mantener propósito, prioridad y límites;
- abrir Conversation Spaces únicamente cuando separarlos aporte valor;
- distinguir hechos, supuestos, propuestas y decisiones;
- aplicar `Memory Bootstrap Gate` antes de depender de historia chat-only;
- decidir si corresponde `Environment Preflight`, `Planning Task` o `Execution Task`;
- seleccionar contexto durable y fuentes suficientes;
- revisar planes, reportes, diffs y evidencia;
- evaluar después qué conocimiento confirmado merece persistirse.

El Project Orchestrator no sustituye la responsabilidad humana ni modifica artefactos físicos por defecto.

## Memoria durable y LLM Wiki

`memoria durable` describe la responsabilidad de conservar conocimiento vigente y reusable fuera de conversaciones efímeras.

`LLM Wiki` es el término de IA-DOS para una materialización durable, portable y navegable de esa memoria para humanos y agentes.

Una LLM Wiki:

- no es obligatoria para toda tarea;
- no exige un repositorio separado;
- no sustituye implementación, backlog o Exchange;
- no debe copiar conversaciones, TASK/REPORT, logs o diffs por defecto;
- debe consumirse selectivamente por los agentes.

## Método de trabajo

La secuencia maestra es:

```text
Dirigir
→ entender
→ decidir
→ delimitar
→ materializar
→ verificar y aprender
```

No son fases rígidas. Memory Bootstrap, Preflight, Planning y Execution se utilizan sólo cuando el siguiente resultado los necesita.

Consulta [Modelo operativo](operating-model.md) y [Método de trabajo](working-method.md).

## Alcance de IA-DOS

IA-DOS puede aplicarse a:

- aplicaciones web y móviles;
- APIs e integraciones;
- automatizaciones;
- agentes y chatbots como productos;
- herramientas internas;
- plataformas SaaS;
- sistemas de datos;
- proyectos nuevos;
- proyectos existentes.

El framework no impone lenguaje, stack, cloud, proveedor de IA, editor, coding agent, topología de repositorios, Wiki o Exchange.

## Formas de consumo

IA-DOS puede consumirse:

- desde el repositorio canónico;
- mediante una referencia local compartida;
- mediante contratos embebidos en tareas;
- mediante el `Current Offline Pack` cuando el repositorio no pueda navegarse;
- mediante una versión o commit adoptado por el proyecto.

El trabajo cotidiano no requiere que cada agente lea IA-DOS completo.

## Fuera de alcance

IA-DOS no:

- decide si una idea de negocio debe construirse;
- reemplaza la dirección humana;
- reemplaza revisión y aprobación humana cuando corresponden;
- programa de forma autónoma sin límites;
- garantiza ausencia de errores;
- sustituye Git, GitHub, Obsidian, backlog o coding agents;
- exige una LLM Wiki completa antes de avanzar;
- exige repositorios separados para app, memoria o Exchange;
- convierte Exchange en workflow, backlog o automatización;
- obliga a abrir una conversación por tarea;
- resuelve por ahora una política universal de persistencia de conversaciones de Planning;
- introduce CLI, agentes propios, watchers, RAG automático o automatización compleja como requisito de la etapa alpha.

## Estado actual

Los fundamentos de `v0.1.0-alpha.1` y la consolidación operacional de `v0.1.0-alpha.2` están completados.

El foco vigente es `v0.1.0-alpha.3 — Real-project adoption`: validar los contratos en proyectos reales, detectar fricción y modificar el método sólo cuando exista evidencia suficiente.

Consulta `../../ROADMAP.md` para el roadmap vigente.

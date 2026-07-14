# Propósito y alcance

## Propósito

IA-DOS es un método operativo abierto para dirigir proyectos de software junto a inteligencia artificial.

Su función no es reemplazar la forma de trabajar de una persona, sino hacerla explícita, reproducible y transferible entre asistentes conversacionales, coding agents, repositorios y herramientas distintas.

IA-DOS ayuda a ordenar:

- la dirección del proyecto;
- la separación de conversaciones por responsabilidad;
- el workspace local;
- la aplicación;
- la memoria durable;
- las instrucciones para agentes;
- el contexto entregado a cada herramienta;
- las tareas;
- las decisiones;
- la ejecución;
- la verificación;
- el aprendizaje acumulado.

El método separa dirección, razonamiento, materialización y verificación para que distintas herramientas colaboren sin crear fuentes de verdad paralelas ni hacer perder el control del proyecto.

## Problema que aborda

Los asistentes conversacionales y coding agents pueden ayudar con gran rapidez, pero no conocen por sí solos:

- el propósito completo del proyecto;
- qué conversación debe tratar cada tema;
- qué decisiones siguen vigentes;
- dónde está la fuente de verdad;
- qué información debe entregarse a un coding agent;
- qué zonas puede modificar;
- qué riesgos debe evitar;
- qué información es real y cuál está planificada;
- qué evidencia se necesita para considerar una tarea terminada.

Sin una estructura común, el desarrollo puede acumular bugs, código innecesario, conversaciones contradictorias, documentación desactualizada y consumo excesivo de contexto.

## Capa de orquestación

IA-DOS reconoce una capa de trabajo anterior a la ejecución técnica.

Esta capa puede vivir en un Project de ChatGPT, un Gem de Gemini, un Project de Claude u otro asistente conversacional.

Su función es:

- comprender el proyecto desde la wiki y las fuentes disponibles;
- capturar dirección y criterio;
- separar conversaciones por dominio cuando reduzca complejidad;
- mantener una visión transversal;
- transformar decisiones y necesidades en `Execution Tasks`;
- preparar prompts optimizados para coding agents;
- seleccionar el contexto mínimo necesario;
- revisar reportes y evidencia;
- indicar qué conocimiento debe volver a la memoria durable.

El Project Orchestrator no reemplaza al coding agent. Piensa, organiza, delimita y revisa; la modificación material de repositorios pertenece a herramientas con acceso controlado de ejecución.

Para muchas personas no programadoras expertas, esta será la interfaz principal de IA-DOS.

## Alcance de IA-DOS

IA-DOS define una forma de trabajo que puede aplicarse a:

- aplicaciones web y móviles;
- APIs e integraciones;
- automatizaciones;
- agentes y chatbots;
- herramientas internas;
- plataformas SaaS;
- sistemas de datos;
- proyectos nuevos;
- proyectos existentes.

El método recomienda prácticas y estructuras. No impone un lenguaje, framework, proveedor cloud, asistente conversacional o coding agent específico.

## Formas de consumo

IA-DOS puede consumirse:

- como repositorio de referencia entregado a un asistente conversacional;
- como repositorio clonado una vez en el workspace local;
- mediante archivos, prompts y plantillas incorporados en cada proyecto;
- mediante una versión publicada y referenciada por el proyecto.

El trabajo cotidiano no requiere que cada agente lea el repositorio completo de IA-DOS. Cada proyecto debe conservar solamente las reglas y el contexto necesarios para la versión adoptada.

## Fuera de alcance

IA-DOS no:

- evalúa si una idea debe construirse;
- define el modelo de negocio;
- reemplaza la dirección humana de producto;
- reemplaza la revisión humana;
- programa de forma autónoma;
- garantiza ausencia de errores;
- sustituye Git, GitHub, Obsidian o las herramientas de desarrollo;
- obliga a reorganizar un proyecto existente sin evaluar el impacto;
- exige que todas las herramientas tengan acceso completo a todos los repositorios.

## Alcance de `v0.1.0-alpha.1`

La primera versión define:

- propósito y público objetivo;
- método de trabajo IA-DOS;
- capa de orquestación conversacional;
- principios y modelo operativo;
- terminología;
- estructura recomendada del workspace;
- forma inicial de adopción;
- guía de construcción de la LLM Wiki;
- prompts iniciales de instalación y handoff;
- guardrails y verificación básica;
- gobierno y contribución.

Los componentes prácticos se agregan en incrementos separados dentro de la misma versión alpha.
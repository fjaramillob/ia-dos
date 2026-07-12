# Propósito y alcance

## Propósito

IA-DOS es una capa operativa común para proyectos de software desarrollados con asistencia de inteligencia artificial.

Su función es ayudar a ordenar:

- la dirección conversacional del proyecto;
- la separación de chats o espacios de trabajo;
- el workspace local;
- la aplicación;
- la memoria del proyecto;
- las instrucciones para agentes;
- el contexto entregado a cada herramienta;
- las tareas;
- las decisiones;
- la verificación;
- el registro del trabajo realizado.

IA-DOS busca que una persona pueda utilizar distintos asistentes y agentes sin depender de conversaciones aisladas ni perder el control del proyecto.

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

- comprender el proyecto desde la wiki y los repositorios;
- ayudar al usuario a separar conversaciones por dominio;
- mantener una visión transversal;
- transformar decisiones y necesidades en `Execution Tasks`;
- preparar prompts optimizados para coding agents;
- seleccionar el contexto mínimo necesario;
- revisar reportes y evidencia;
- indicar qué debe actualizarse en la wiki.

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

El framework recomienda prácticas y estructuras. No impone un lenguaje, framework, proveedor cloud, asistente conversacional o coding agent específico.

## Formas de consumo

IA-DOS puede consumirse:

- como repositorio de referencia entregado a ChatGPT, Gemini, Claude u otro asistente;
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
- capa de orquestación conversacional;
- principios y modelo operativo básico;
- terminología;
- estructura recomendada del workspace;
- forma inicial de adopción;
- guía de construcción de la LLM Wiki;
- prompts iniciales de instalación y handoff;
- guardrails y verificación básica;
- gobierno y contribución.

Los componentes prácticos se agregarán en incrementos separados dentro de la misma versión alpha.
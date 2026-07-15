# Propósito y alcance

## Propósito

IA-DOS es una capa operativa común para proyectos de software desarrollados con asistencia de inteligencia artificial.

Su función es coordinar:

- la dirección humana del proyecto;
- la orquestación conversacional;
- el razonamiento especializado por dominio;
- la memoria durable;
- la delimitación del trabajo;
- la materialización mediante coding agents;
- la verificación basada en evidencia;
- el aprendizaje que regresa a las fuentes de verdad.

IA-DOS busca que una persona pueda utilizar distintos asistentes y agentes sin depender de conversaciones aisladas, crear fuentes de verdad paralelas ni perder el control del proyecto.

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

## Separación de funciones

IA-DOS separa cuatro funciones que suelen mezclarse:

```text
Dirección
→ razonamiento
→ materialización
→ verificación
```

- La persona responsable define propósito, prioridades, restricciones y autoridad.
- El Project Orchestrator organiza, decide con la persona, delimita y revisa.
- Los Conversation Spaces razonan sobre dominios concretos cuando son útiles.
- Los coding agents modifican artefactos reales, ejecutan pruebas y entregan evidencia.
- GitHub u otro sistema de control de versiones traza los cambios.
- La LLM Wiki conserva contexto, decisiones y estado durable.

Esta separación evita que una conversación sea confundida con una implementación o que un agente de ejecución tome decisiones que no le corresponden.

## Capa de orquestación

IA-DOS reconoce una capa de trabajo anterior y posterior a la ejecución técnica.

Puede vivir en un Project de ChatGPT, un Gem de Gemini, un Project de Claude u otro asistente conversacional.

Su función es:

- comprender el proyecto desde la wiki, repositorios y fuentes disponibles;
- capturar el alma y la dirección;
- ayudar al usuario a separar conversaciones por dominio;
- mantener una visión transversal;
- distinguir hechos, hipótesis, propuestas y decisiones;
- transformar decisiones y necesidades en `Execution Tasks`;
- preparar handoffs optimizados para coding agents;
- seleccionar el contexto mínimo necesario;
- revisar reportes, diffs y evidencia;
- indicar qué conocimiento confirmado debe actualizarse en la memoria durable.

El Project Orchestrator define qué debe cambiar y por qué. La modificación física corresponde a un coding agent o herramienta con capacidad adecuada.

Para muchas personas no programadoras expertas, esta será la interfaz principal de IA-DOS.

## Método de trabajo

IA-DOS utiliza cinco movimientos iterativos:

```text
Entender
→ decidir
→ delimitar
→ materializar
→ verificar y aprender
```

No son fases rígidas. La documentación y la wiki acompañan el ciclo en lugar de convertirse en una etapa pesada previa a construir.

Consulta [Método de trabajo](working-method.md).

## Alcance de IA-DOS

IA-DOS puede aplicarse a:

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

- como repositorio de referencia entregado a un asistente;
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
- programa de forma autónoma sin límites ni supervisión;
- garantiza ausencia de errores;
- sustituye Git, GitHub, Obsidian o las herramientas de desarrollo;
- obliga a reorganizar un proyecto existente sin evaluar el impacto;
- exige que todas las herramientas tengan acceso completo a todos los repositorios;
- convierte un asistente conversacional en ejecutor cuando no tiene acceso real a los artefactos.

## Alcance de `v0.1.0-alpha.1`

La primera versión define:

- propósito y público objetivo;
- método de trabajo maestro;
- capa de orquestación conversacional;
- responsabilidades humanas, del Orchestrator y de coding agents;
- principios y modelo operativo;
- terminología;
- estructura recomendada del workspace;
- forma inicial de adopción;
- guía de construcción de la LLM Wiki;
- prompts iniciales de instalación y handoff;
- guardrails y verificación básica;
- gobierno y contribución.

Los componentes prácticos se agregan en incrementos separados dentro de la misma versión alpha.
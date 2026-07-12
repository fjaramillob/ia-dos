# IA-DOS

**Intelligence-Assisted Development Operating System**

Framework abierto para organizar proyectos de software desarrollados con asistencia de inteligencia artificial.

IA-DOS entrega una forma común de coordinar:

- la persona que dirige el proyecto;
- ChatGPT, Gemini, Claude u otros asistentes conversacionales;
- Codex, Claude Code, Antigravity u otros coding agents;
- la LLM Wiki del proyecto;
- el repositorio de aplicación;
- las tareas, decisiones, pruebas y revisiones.

## Qué problema resuelve

Cuando un proyecto se desarrolla con varios chats, agentes y herramientas, suelen aparecer problemas como:

- contexto fragmentado;
- decisiones perdidas;
- código que no se termina usando;
- cambios fuera de alcance;
- bugs introducidos por modificaciones no controladas;
- prompts repetidos;
- consumo innecesario de tokens;
- documentación desactualizada;
- conversaciones que actúan como memorias paralelas;
- dificultad para saber qué está realmente terminado.

IA-DOS busca reducir estos problemas mediante una estructura simple, explícita y reutilizable.

## Para quién está pensado

IA-DOS está dirigido principalmente a personas que ya están construyendo con inteligencia artificial.

El usuario puede no ser un programador experto, pero normalmente:

- entiende conceptos generales de sistemas;
- puede describir qué necesita construir;
- toma decisiones de producto o tecnología;
- utiliza un Project de ChatGPT, un Gem de Gemini u otro asistente para dirigir el proyecto;
- utiliza Codex, Claude Code, Antigravity u otros agentes para desarrollar;
- trabaja con repositorios, aplicaciones, APIs, bases de datos o automatizaciones;
- necesita mantener control sobre lo que los agentes leen, cambian y reportan.

## La capa de orquestación

Para muchos usuarios, la interfaz principal de IA-DOS será un asistente conversacional externo al código.

Ese asistente funciona como **Project Orchestrator**:

- comprende el proyecto mediante su wiki y repositorios;
- propone una separación clara de conversaciones por dominio;
- ayuda a tomar decisiones y registrar sus resultados;
- transforma necesidades en `Execution Tasks`;
- prepara prompts optimizados para coding agents;
- selecciona solo el contexto necesario;
- revisa los reportes de ejecución y solicita evidencia;
- mantiene alineados la conversación, la wiki y el desarrollo.

Consulta [ORCHESTRATOR.md](ORCHESTRATOR.md) para las instrucciones dirigidas a ChatGPT, Gemini, Claude u otros asistentes equivalentes.

## Qué propone

IA-DOS organiza cinco elementos principales:

1. **Orquestación conversacional:** un espacio de dirección que convierte conversaciones en inputs estructurados para el desarrollo.
2. **Workspace ordenado:** una ubicación clara para IA-DOS y para cada proyecto.
3. **Memoria durable:** una LLM Wiki versionada que conserva contexto, decisiones y estado real.
4. **Ejecución acotada:** tareas pequeñas, con alcance, límites y criterios de aceptación.
5. **Verificación con evidencia:** un trabajo no se considera terminado solo porque un agente lo afirma.

## Estructura recomendada

```text
proyectos/
├── 00-ia-dos/
└── nombre-proyecto/
    ├── nombre-proyecto-app/
    └── nombre-proyecto-wiki/
```

- `00-ia-dos/` contiene el framework común.
- `nombre-proyecto-app/` contiene la implementación.
- `nombre-proyecto-wiki/` contiene la memoria durable del proyecto.

Esta es una arquitectura de referencia fuertemente recomendada, no una obligación. Los proyectos existentes, monorepos o estructuras especiales pueden adoptar IA-DOS mediante excepciones documentadas.

## Cómo funciona

```text
Conversar y dirigir
→ entender
→ documentar
→ delimitar
→ ejecutar
→ verificar
→ registrar
```

La conversación es un espacio de dirección y trabajo. La wiki, el código, los issues, las decisiones y los pull requests conservan los resultados durables.

## Flujo entre asistentes y desarrollo

```text
Usuario
   ↓
ChatGPT / Gemini / Claude
Project Orchestrator
   ↓
LLM Wiki + contexto seleccionado
   ↓
Execution Task + prompt optimizado
   ↓
Codex / Claude Code / Antigravity
   ↓
Código + pruebas + reporte
   ↓
Revisión y actualización de la wiki
```

El orquestador no debe reenviar toda la historia o todos los repositorios para cada tarea. Debe utilizar un contexto `CORE`, uno o dos `Context Packs` relevantes y una `Execution Task` acotada.

## Cómo se consume IA-DOS

IA-DOS puede utilizarse de dos formas complementarias:

- **Como repositorio de referencia para ChatGPT, Gemini u otro asistente:** el sistema lee IA-DOS para conocer cómo debe orquestar el proyecto.
- **Como instalación local del workspace:** se clona una vez como `proyectos/00-ia-dos/` para consultar documentación, prompts y plantillas.

No se copia el repositorio completo dentro de cada proyecto. Cada proyecto conserva solamente su wiki, sus instrucciones y la configuración correspondiente a la versión adoptada.

Para que un asistente externo pueda orquestar un proyecto concreto debe recibir, además de IA-DOS:

- acceso o referencia a la wiki del proyecto;
- acceso o referencia al repositorio de aplicación cuando corresponda;
- las instrucciones específicas del usuario o equipo;
- la versión de IA-DOS adoptada.

## Qué no es

IA-DOS no es:

- un evaluador de ideas o proyectos;
- una herramienta que programa por sí sola;
- un agente autónomo que elimina la supervisión humana;
- una aplicación SaaS;
- un reemplazo de GitHub, Obsidian, Spec Kit, OpenSpec o los agentes de desarrollo;
- una garantía de que un proyecto estará libre de errores.

## Estado actual

El proyecto se encuentra en fase fundacional. La primera versión será `v0.1.0-alpha.1` y se centrará en:

- propósito y alcance;
- público objetivo;
- orquestación conversacional;
- principios y modelo operativo;
- estructura del workspace;
- construcción inicial de la LLM Wiki;
- adopción por proyectos;
- prompts de instalación, clonación y handoff hacia coding agents;
- plantillas mínimas;
- guardrails y verificación inicial.

Consulta [docs/index.md](docs/index.md) para navegar la documentación.

## Licencia

IA-DOS se distribuye bajo la licencia [Apache License 2.0](LICENSE).
# Conectores y MCP para GitHub

IA-DOS puede operar con asistentes conversacionales, coding agents y herramientas que acceden a GitHub mediante conectores, integraciones nativas o servidores MCP.

El objetivo no es obligar a una tecnología específica. El objetivo es asegurar que la LLM Wiki y el repositorio de aplicación puedan leerse y actualizarse de forma controlada, verificable y trazable.

## Principio operativo

El asistente conversacional coordina y prepara el trabajo. El coding agent o herramienta con acceso efectivo al repositorio ejecuta los cambios.

```text
00 / 10 / 20 / 90
→ contexto, decisión o propuesta
→ Execution Task o Wiki Update Task
→ Codex, Antigravity, Claude Code u otro agente con acceso al repositorio
→ rama, cambios, pruebas y validaciones
→ PR o diff revisable
→ Execution Report
→ actualización de la LLM Wiki cuando corresponda
```

Un Project, Gem o chat no debe asumir que puede escribir en GitHub solo porque puede leerlo.

## Casos de uso

### Actualizar la LLM Wiki

`90 — Wiki y memoria` prepara:

- objetivo de la actualización;
- páginas y rutas relevantes;
- hechos, decisiones e hipótesis que deben registrarse;
- archivos autorizados;
- fuera de alcance;
- validaciones de Markdown, YAML y enlaces;
- condición de detención;
- evidencia esperada.

Después entrega una tarea acotada al coding agent. El agente trabaja sobre el repositorio de la wiki, no sobre la conversación.

### Actualizar el repositorio de aplicación

`30 — Ejecución y desarrollo` prepara una `Execution Task` con:

- objetivo;
- contexto mínimo desde la wiki;
- rutas autorizadas;
- cambios permitidos;
- fuera de alcance;
- criterios de aceptación;
- pruebas;
- condiciones de detención;
- evidencia esperada.

El coding agent ejecuta y devuelve un `Execution Report`.

## Capacidades mínimas recomendadas

Una integración con GitHub debería permitir, según el nivel de autorización:

### Lectura

- listar repositorios y ramas;
- leer archivos por ruta y ref;
- inspeccionar commits, issues y pull requests;
- comparar cambios;
- revisar estado de CI y evidencia.

### Escritura controlada

- crear ramas;
- crear o actualizar archivos;
- crear commits;
- abrir pull requests;
- comentar o actualizar issues;
- consultar y resolver observaciones de revisión;
- fusionar solo con autorización separada cuando corresponda.

No todas las herramientas necesitan permisos de escritura. Un flujo puede usar una herramienta de solo lectura para diagnosticar y otra para ejecutar.

## Conectores nativos

Algunas plataformas ofrecen conectores directos a GitHub. Antes de usarlos, confirma:

- qué repositorios puede leer;
- si puede escribir;
- si escribe directamente en la rama principal;
- si puede crear ramas y pull requests;
- qué identidad realiza los commits;
- si registra auditoría;
- cómo se revocan los permisos;
- si respeta repositorios privados;
- si puede operar sobre más de un repositorio del mismo proyecto.

La autorización conceptual de una estrategia no equivale a autorización para usar el conector y modificar un repositorio.

## MCP

MCP puede exponer herramientas de GitHub a un asistente o coding agent. IA-DOS no depende de un servidor MCP concreto.

Antes de habilitar un servidor MCP para GitHub, define:

- host y proveedor confiable;
- repositorios autorizados;
- operaciones permitidas;
- alcance de los tokens;
- tratamiento de secretos;
- modo de aprobación para escritura;
- política de ramas y pull requests;
- logs y trazabilidad;
- revocación y rotación de credenciales.

Preferencias recomendadas:

```text
lectura amplia solo cuando sea necesaria
+
escritura limitada a repositorios específicos
+
rama de trabajo
+
PR revisable
+
merge separado
```

Evita entregar tokens personales de alcance amplio dentro de prompts, archivos de configuración versionados o la LLM Wiki.

## Configuración por herramienta

La configuración exacta cambia entre Codex, Antigravity, Claude Code, VS Code, IDEs y plataformas conversacionales. Documenta en el proyecto:

- herramienta utilizada;
- método de acceso: local, conector o MCP;
- repositorios disponibles;
- nivel de permisos;
- comandos o acciones verificadas;
- limitaciones conocidas;
- responsable de aprobar escritura y merge.

No declares una integración como operativa hasta verificar al menos una lectura y, cuando corresponda, una escritura controlada en una rama de prueba.

## Flujo recomendado para la LLM Wiki

```text
90 prepara una Wiki Update Task
→ persona revisa alcance
→ autoriza ejecución
→ coding agent lee IA-DOS + CORE + páginas relevantes
→ crea rama en el repositorio de la wiki
→ aplica solo cambios autorizados
→ valida Markdown, YAML, enlaces y estado
→ abre PR
→ entrega Execution Report
→ 90 revisa el resultado y consolida el siguiente aprendizaje
```

`90` no necesita realizar personalmente las operaciones GitHub. Su responsabilidad principal es producir contexto y criterios suficientemente claros para que el agente ejecutor mantenga la wiki correctamente.

## Flujo recomendado para la aplicación

```text
30 prepara una Execution Task
→ coding agent lee CORE y Context Pack relevante
→ crea rama en el repositorio de aplicación
→ implementa dentro del alcance
→ ejecuta pruebas
→ abre PR
→ entrega Execution Report
→ 00 revisa dirección y 90 registra aprendizaje durable
```

## Guardrails

- usa permisos mínimos;
- nunca almacenes tokens o secretos en la wiki;
- no escribas directamente en `main` salvo política explícita y cambio de riesgo mínimo;
- separa autorización de cambio y autorización de merge;
- valida el artefacto antes de declararlo terminado;
- no permitas que un agente modifique simultáneamente app y wiki sin que la tarea lo autorice;
- registra repositorio, rama, archivos, commit, pruebas y PR;
- detente ante contradicciones, cambios locales desconocidos o falta de acceso.

## Evidencia esperada

Toda ejecución debe poder responder:

- qué repositorio se modificó;
- qué rama se utilizó;
- qué archivos cambiaron;
- qué commit o PR contiene el resultado;
- qué validaciones se ejecutaron;
- qué riesgos o pendientes quedaron;
- qué actualización requiere la wiki.

## Resultado esperado

Los conectores y MCP deben reducir fricción operacional sin convertir al asistente conversacional en un ejecutor opaco. IA-DOS mantiene la separación entre coordinación, ejecución, revisión y memoria durable.
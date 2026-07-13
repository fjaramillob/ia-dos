# Inicializar el Project Orchestrator

Este recorrido permite configurar IA-DOS dentro de un Project de ChatGPT, un Gem de Gemini, un Project de Claude o un entorno conversacional equivalente.

## Repositorio oficial

```text
https://github.com/fjaramillob/ia-dos
```

El asistente no debe asumir que conoce IA-DOS por nombre. Debe consultar el repositorio oficial o recibir el pack de contexto antes de aplicar el framework.

## Vista rápida

Configura cuatro elementos:

1. nombre y descripción del espacio;
2. instrucciones persistentes;
3. conocimientos o archivos;
4. primer mensaje.

No mezcles en las instrucciones persistentes tareas actuales, prioridades semanales, estados cambiantes ni decisiones temporales.

## 1. Nombre y descripción del espacio

Nombre sugerido:

```text
[NOMBRE DEL PROYECTO]
```

Descripción sugerida:

```text
Project Orchestrator de [NOMBRE DEL PROYECTO], configurado con IA-DOS para dirigir decisiones, memoria, tareas y desarrollo asistido por IA.
```

## 2. Instrucciones persistentes

Copia este bloque en el campo **Instrucciones** del Project, Gem o espacio equivalente:

```text
Actúa como Project Orchestrator de [NOMBRE DEL PROYECTO] utilizando IA-DOS como marco operativo.

Repositorio oficial de IA-DOS:
https://github.com/fjaramillob/ia-dos

Antes de aplicar IA-DOS:
1. intenta consultar el repositorio oficial y leer README.md, ORCHESTRATOR.md y docs/index.md;
2. si no puedes acceder, busca entre los conocimientos adjuntos ia-dos-project-orchestrator-pack.md;
3. si tampoco está disponible, indícalo y solicita ese pack o los tres archivos anteriores;
4. no asumas que conoces IA-DOS solo por su nombre.

Fuentes de verdad:
- IA-DOS define cómo trabajar;
- la LLM Wiki del proyecto conserva propósito, decisiones, arquitectura y estado contextual;
- el repositorio de aplicación conserva la implementación real;
- la fuente canónica de tareas debe declararse explícitamente.

Forma de trabajo:
- lee primero todas las fuentes entregadas;
- extrae de ellas propósito, usuario, problema, alcance, activos existentes, restricciones, decisiones, supuestos y preguntas abiertas;
- no vuelvas a preguntar algo que ya esté respondido por una fuente;
- distingue hechos, preferencias, supuestos, propuestas y decisiones confirmadas;
- no presentes como implementado algo que no tenga evidencia;
- clasifica el estado del producto objetivo, no el de sistemas anteriores mencionados como contexto;
- utiliza el contexto mínimo necesario;
- no trates los chats como memoria durable;
- registra decisiones durables en la wiki o ADR correspondiente;
- convierte el trabajo de desarrollo en Execution Tasks acotadas;
- define alcance, fuera de alcance, criterios de aceptación, pruebas y condiciones de detención;
- exige evidencia antes de cerrar una tarea;
- no modifiques repositorios, producción, costes o recursos externos sin autorización explícita;
- detente ante contradicciones, falta de acceso, riesgos críticos o decisiones importantes no resueltas.

Conversation Spaces:
- mantén 00 — Dirección y orquestación como conversación principal;
- en proyectos nuevos, 00 comienza como Dirección y definición;
- en proyectos existentes, 00 comienza como Descubrimiento y adopción;
- utiliza 90 — Wiki y memoria para consolidar conocimiento durable;
- agrega 30 — Ejecución y desarrollo cuando comience el trabajo técnico;
- crea conversaciones adicionales solo cuando reduzcan mezcla de contexto o exista actividad recurrente;
- no abras una conversación por cada dominio de forma automática;
- no simules 90 como una sección dentro de 00; propón una conversación separada cuando corresponda, salvo que la plataforma no lo permita.

Relación con coding agents:
- un Conversation Space puede originar múltiples Execution Tasks;
- cada Execution Task debe corresponder a una ejecución acotada y verificable de Codex, Antigravity, Claude Code u otro coding agent;
- cada ejecución debe devolver un Execution Report;
- las sesiones del coding agent no son la memoria canónica del proyecto.

Antes de actuar, confirma qué fuentes están disponibles y qué escenario aplica. Cuando falte información crítica, indícalo en lugar de inventarla.
```

Personaliza únicamente:

- `[NOMBRE DEL PROYECTO]`;
- enlaces o rutas breves hacia la wiki y el repositorio;
- la fuente canónica de tareas;
- restricciones estables de seguridad, coste o cumplimiento.

## 3. Conocimientos o archivos del espacio

Carga preferentemente:

```text
1. IA-DOS Project Orchestrator Pack
2. una descripción o Project Intake Brief del proyecto
3. repositorio, wiki, documentos, enlaces o reportes disponibles
```

### Dónde obtener el pack

El pack está dentro del repositorio oficial:

[Descargar o abrir IA-DOS Project Orchestrator Pack](../../bundles/ia-dos-project-orchestrator-pack.md)

Ruta dentro del repositorio:

```text
bundles/ia-dos-project-orchestrator-pack.md
```

En GitHub:

1. abre el enlace anterior;
2. presiona **Download raw file** o abre **Raw**;
3. guarda el archivo como `ia-dos-project-orchestrator-pack.md`;
4. súbelo al área **Conocimientos** del Project, Gem o espacio equivalente.

También puedes descargar todo el repositorio como ZIP y extraer ese archivo desde la carpeta `bundles/`.

El pack resuelve el caso en que la plataforma no puede navegar GitHub. Es un artefacto de distribución; el repositorio oficial sigue siendo la fuente canónica.

La descripción del proyecto puede ser un PDF, documento, wiki o la plantilla:

[Project Intake Brief](../../templates/project-intake-brief.template.md)

Como mínimo debería permitir entender:

- nombre del proyecto;
- estado del producto objetivo: nuevo o existente;
- propósito;
- usuario principal;
- problema;
- alcance inicial;
- activos que ya existen;
- sistemas anteriores relacionados y su relación;
- restricciones;
- fuentes disponibles.

No es necesario completar todo para comenzar. Los vacíos deben marcarse como `Desconocido` y preguntarse de forma progresiva.

## 4. Primer mensaje

Copia este bloque en la primera conversación:

```text
Inicia este proyecto aplicando IA-DOS.

Proyecto: [NOMBRE DEL PROYECTO]

Descripción inicial:
- [RESUMEN BREVE O Disponible en el archivo NOMBRE-DEL-ARCHIVO]

Fuentes disponibles del proyecto:
- [REPOSITORIO, WIKI, DOCUMENTOS, URL O Ninguna todavía]

Antes de proponer desarrollo:
1. lee todas las fuentes disponibles;
2. extrae propósito, usuario, problema, alcance, fuera de alcance, activos existentes, sistemas relacionados, restricciones, decisiones, supuestos y preguntas abiertas;
3. no repitas preguntas ya respondidas por las fuentes;
4. determina si el producto objetivo es nuevo o existente;
5. no clasifiques el proyecto como existente solo porque menciona un sistema anterior, migración o producto relacionado.

Si el producto objetivo es nuevo:
- utiliza esta conversación como 00 — Dirección y definición;
- guía preguntas progresivas solo sobre vacíos importantes;
- no selecciones stack ni solicites construir la aplicación completa antes de contar con decisiones suficientes;
- al terminar la definición inicial, entrega una síntesis estructurada y propón crear una conversación separada 90 — Wiki y memoria.

Si el producto objetivo es existente:
- utiliza esta conversación como 00 — Descubrimiento y adopción;
- reconstruye el estado actual sin modificar archivos ni inventar historia;
- verifica si existe una LLM Wiki usable;
- si no existe, propón una conversación separada 90 — Wiki y memoria y constrúyela desde evidencia.

Comienza confirmando:
1. si pudiste acceder al repositorio IA-DOS o al pack de contexto;
2. qué fuentes del proyecto están disponibles;
3. el escenario detectado y su evidencia;
4. el primer paso recomendado.
```

## Resultado esperado

El onboarding está completo cuando el asistente:

- reconoce su rol como Project Orchestrator;
- puede operar aunque no tenga acceso directo a GitHub;
- comprende el proyecto sin exigir un formulario pesado;
- clasifica correctamente el producto objetivo;
- evita repetir preguntas ya respondidas;
- comienza en `00` y separa `90` cuando corresponda;
- no salta prematuramente al código;
- convierte la conversación en memoria durable y trabajo de desarrollo estructurado.

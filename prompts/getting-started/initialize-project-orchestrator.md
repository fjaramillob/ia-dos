# Inicializar el Project Orchestrator

Este recorrido permite configurar IA-DOS dentro de un Project de ChatGPT, un Gem de Gemini, un Project de Claude o un entorno conversacional equivalente.

## Repositorio oficial

```text
https://github.com/fjaramillob/ia-dos
```

El repositorio oficial es la fuente canónica. Cuando la plataforma no pueda navegar GitHub, `ia-dos-project-orchestrator-pack.md` funciona como fuente operativa.

## Vista rápida

Configura:

1. nombre y descripción del espacio;
2. instrucciones persistentes;
3. conocimientos o archivos;
4. primer mensaje.

## 1. Nombre y descripción

Nombre sugerido:

```text
[NOMBRE DEL PROYECTO]
```

Descripción sugerida:

```text
Project Orchestrator de [NOMBRE DEL PROYECTO], configurado con IA-DOS para transformar dirección, decisiones y aprendizaje en avances concretos de producto y desarrollo.
```

## 2. Instrucciones persistentes

Copia [Instrucciones persistentes](../../templates/project-instructions.template.md) en el campo correspondiente.

Personaliza solo nombre, rutas breves, fuente canónica de tareas y restricciones estables.

## 3. Conocimientos o archivos

Carga preferentemente:

```text
1. IA-DOS Project Orchestrator Pack
2. descripción o Project Intake Brief
3. repositorio, wiki, documentos, enlaces o reportes disponibles
```

[Descargar o abrir IA-DOS Project Orchestrator Pack](../../bundles/ia-dos-project-orchestrator-pack.md)

Ruta:

```text
bundles/ia-dos-project-orchestrator-pack.md
```

La descripción puede ser un PDF, documento, wiki o [Project Intake Brief](../../templates/project-intake-brief.template.md). No es necesario completar todo para comenzar.

## 4. Primer mensaje

```text
Inicia este proyecto aplicando IA-DOS.

Proyecto: [NOMBRE DEL PROYECTO]

Descripción inicial:
- [RESUMEN BREVE O Disponible en el archivo NOMBRE-DEL-ARCHIVO]

Fuentes disponibles:
- [REPOSITORIO, WIKI, DOCUMENTOS, URL O Ninguna todavía]

Antes de proponer desarrollo:
1. lee todas las fuentes;
2. clasifica el producto objetivo como nuevo o existente;
3. no lo clasifiques como existente solo por mencionar un sistema anterior;
4. no repitas preguntas respondidas por las fuentes.

Si es nuevo:
- utiliza esta conversación como 00 — Dirección y definición;
- captura propósito, usuario, problema, promesa, principios, primer resultado y límites;
- no intentes definir todo antes de avanzar;
- marca lo pendiente como hipótesis, pregunta abierta o decisión por explorar.

Cuando diga “avancemos”, “empecemos a armar”, “ya tenemos suficiente” o equivalente, activa Launch Mode:
- deja de repetir el diagnóstico;
- presenta la dirección capturada;
- propone una estrategia ordenada;
- indica qué conversaciones crear ahora y cuáles después;
- entrega un Conversation Space Handoff autosuficiente para cada conversación nueva;
- define el primer avance concreto.

Secuencia frecuente para un proyecto nuevo:

Crear ahora:
- 90 — Wiki y memoria
- 10 — Producto y UX

Crear después de recibir el handoff de 10:
- 20 — Arquitectura y stack

Crear después de recibir el handoff de 20:
- 30 — Ejecución y desarrollo

No abras todas las conversaciones a la vez sin declarar dependencias.

Dentro de un Project o Gem dedicado a un solo proyecto, usa títulos limpios sin agregar “: [NOMBRE DEL PROYECTO]”, salvo necesidad real de desambiguación.

Cada prompt para una conversación nueva debe comenzar declarando:

Esta conversación es [NOMBRE DEL ESPACIO].
No reinicies el onboarding.
No reclasifiques el proyecto.
No propongas renombrar este chat como 00.
No repitas la configuración inicial de IA-DOS.

Después incluye:
- dirección del proyecto;
- decisiones confirmadas;
- hipótesis o referencias no confirmadas;
- preguntas abiertas relevantes;
- fuentes disponibles;
- objetivo;
- entregable esperado;
- fuera de alcance.

No asumas que las conversaciones comparten historial.

Regla especial para 20 — Arquitectura y stack:
- debe recibir el handoff de 10;
- no debe asumir stack por antecedentes;
- Supabase, TypeScript, RLS u otras tecnologías heredadas son referencias no confirmadas salvo decisión explícita;
- debe recomendar arquitectura suficiente para el primer vertical slice, con alternativas y trade-offs.

Cada espacio debe cerrar un hito con un Handoff de salida que incluya resultado, decisiones, pendientes, artefactos y contexto para el siguiente espacio.

En tu primera respuesta:
- informa fuente operativa y canónica;
- resume fuentes;
- clasifica el producto y explica evidencia;
- indica el nombre recomendado de esta conversación;
- entrega un diagnóstico breve;
- formula una pregunta prioritaria;
- termina con Tu siguiente acción.

En respuestas posteriores:
- no repitas Configuración inicial ni la instrucción para renombrar;
- actualiza el estado de decisiones;
- no describas al usuario como bloqueo;
- si delega una decisión a mejores prácticas, recomienda una opción provisional y continúa salvo riesgo crítico;
- prioriza estrategia, siguiente paso y resultados concretos.
```

## Plantilla para abrir una conversación especializada

Usa [Conversation Space Handoff](../../templates/conversation-space-handoff.template.md).

El título del chat debe coincidir exactamente con el destino indicado en el handoff.

## Resultado esperado

El onboarding está bien encaminado cuando el asistente:

- comprende el espíritu del proyecto;
- propone una estrategia;
- activa Launch Mode;
- abre los espacios en un orden explícito;
- transfiere contexto sin depender del historial entre chats;
- evita heredar decisiones técnicas no confirmadas;
- conecta producto, arquitectura, wiki, ejecución y coding agents.
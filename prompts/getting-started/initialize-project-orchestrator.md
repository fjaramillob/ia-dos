# Inicializar el Project Orchestrator

Este recorrido permite configurar IA-DOS dentro de un Project de ChatGPT, un Gem de Gemini, un Project de Claude o un entorno conversacional equivalente.

## Repositorio oficial

```text
https://github.com/fjaramillob/ia-dos
```

El repositorio oficial es la **fuente canónica** de IA-DOS. Cuando la plataforma no pueda navegar GitHub, `ia-dos-project-orchestrator-pack.md` funciona como **fuente operativa** para esa sesión.

El asistente no debe presentar el pack como fuente canónica ni asumir que conoce IA-DOS solo por su nombre.

## Vista rápida

Configura cuatro elementos:

1. nombre y descripción del espacio;
2. instrucciones persistentes;
3. conocimientos o archivos;
4. primer mensaje.

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

Copia el bloque de [instrucciones persistentes](../../templates/project-instructions.template.md) en el campo **Instrucciones** del Project, Gem o espacio equivalente.

Personaliza únicamente:

- nombre del proyecto;
- enlaces o rutas breves hacia wiki y repositorio;
- fuente canónica de tareas;
- restricciones estables de seguridad, coste o cumplimiento.

No agregues tareas actuales, prioridades semanales, estado cambiante, secretos ni copias completas de la wiki.

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

Ruta:

```text
bundles/ia-dos-project-orchestrator-pack.md
```

En GitHub:

1. abre el enlace;
2. presiona **Download raw file** o abre **Raw**;
3. guarda el archivo como `ia-dos-project-orchestrator-pack.md`;
4. súbelo al área **Conocimientos** del Project, Gem o espacio equivalente.

El pack es un artefacto de distribución. El repositorio oficial sigue siendo la fuente canónica.

La descripción del proyecto puede ser un PDF, documento, wiki o la plantilla [Project Intake Brief](../../templates/project-intake-brief.template.md).

Como mínimo debería permitir entender:

- nombre del proyecto;
- estado del producto objetivo: nuevo o existente;
- propósito;
- usuario principal;
- problema;
- alcance inicial;
- activos existentes;
- sistemas relacionados y su relación;
- restricciones;
- fuentes disponibles.

No es necesario completar todo para comenzar. Los vacíos deben marcarse como `Desconocido` y resolverse progresivamente.

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
- resuelve por defecto una decisión principal por turno;
- usa los niveles de definición como guía interna, pero habla conmigo en lenguaje natural;
- comienza por el resultado esperado y no saltes prematuramente a interfaz, arquitectura o implementación;
- no propongas porcentajes, días, semanas o umbrales sin evidencia;
- no selecciones stack ni solicites construir la aplicación completa antes de contar con decisiones suficientes;
- no cierres 00 ni propongas 90 hasta contar con una síntesis suficiente y aprobación explícita.

Si el producto objetivo es existente:
- utiliza esta conversación como 00 — Descubrimiento y adopción;
- reconstruye el estado actual sin modificar archivos ni inventar historia;
- verifica si existe una LLM Wiki usable;
- si no existe, registra esa necesidad, pero no la conviertas automáticamente en la siguiente acción antes de completar el diagnóstico.

En tu primera respuesta:
- informa qué fuente operativa de IA-DOS utilizaste;
- indica que la fuente canónica es https://github.com/fjaramillob/ia-dos;
- resume las fuentes del proyecto;
- clasifica el producto objetivo y explica brevemente la evidencia;
- indica de forma visible el nombre recomendado para esta conversación;
- pide al usuario renombrarla manualmente cuando la plataforma lo permita;
- entrega un diagnóstico breve, no una auditoría extensa;
- formula una sola pregunta prioritaria por defecto;
- termina con una sección Tu siguiente acción.

En respuestas posteriores:
- no repitas Configuración inicial ni la instrucción para renombrar salvo que cambie el escenario;
- actualiza inmediatamente el estado de las propuestas confirmadas;
- no describas al usuario como bloqueo;
- etiqueta las alternativas como propuestas pendientes de confirmación;
- evita lenguaje de implementación antes de una Execution Task aprobada;
- no mezcles decisiones distintas en una misma pregunta;
- no anuncies 90 — Wiki y memoria como siguiente paso automático por responder una o dos preguntas.
```

## Forma esperada de la primera respuesta

La primera respuesta debe usar Markdown normal, ser breve y seguir este orden:

```text
Configuración inicial
- Fuente operativa utilizada
- Fuente canónica de IA-DOS
- Fuentes del proyecto
- Producto objetivo y evidencia

Nombre de esta conversación
Renombra este chat como:
00 — Dirección y definición

Lo que ya entendí
- síntesis breve

Lo que falta resolver ahora
- una decisión prioritaria

Tu siguiente acción
1. renombra la conversación;
2. confirma o corrige la clasificación;
3. responde una pregunta concreta.
```

Para un producto existente utiliza `00 — Descubrimiento y adopción`.

## Resultado esperado

El onboarding está completo cuando el asistente:

- reconoce su rol como Project Orchestrator;
- distingue fuente canónica y fuente operativa;
- puede operar aunque no tenga acceso directo a GitHub;
- comprende el proyecto sin exigir un formulario pesado;
- clasifica correctamente el producto objetivo;
- evita repetir preguntas ya respondidas;
- mantiene correctamente el estado de propuestas y decisiones;
- guía una decisión principal por turno con lenguaje natural;
- no inventa métricas ni salta prematuramente a diseño o implementación;
- comienza en `00` y separa `90` solo cuando corresponde;
- convierte la conversación en memoria durable y trabajo de desarrollo estructurado.

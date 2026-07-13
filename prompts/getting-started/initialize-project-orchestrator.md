# Inicializar el Project Orchestrator

Este recorrido permite configurar IA-DOS dentro de un Project de ChatGPT, un Gem de Gemini, un Project de Claude o un entorno conversacional equivalente.

## Repositorio oficial

```text
https://github.com/fjaramillob/ia-dos
```

El repositorio oficial es la fuente canónica de IA-DOS. Cuando la plataforma no pueda navegar GitHub, `ia-dos-project-orchestrator-pack.md` funciona como fuente operativa para esa sesión.

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
Project Orchestrator de [NOMBRE DEL PROYECTO], configurado con IA-DOS para transformar dirección, decisiones y aprendizaje en avances concretos de producto y desarrollo.
```

## 2. Instrucciones persistentes

Copia la plantilla [Instrucciones persistentes](../../templates/project-instructions.template.md) en el campo **Instrucciones** del Project, Gem o espacio equivalente.

Personaliza únicamente:

- nombre del proyecto;
- enlaces o rutas breves hacia wiki y repositorio;
- fuente canónica de tareas;
- restricciones estables de seguridad, coste o cumplimiento.

## 3. Conocimientos o archivos del espacio

Carga preferentemente:

```text
1. IA-DOS Project Orchestrator Pack
2. una descripción o Project Intake Brief del proyecto
3. repositorio, wiki, documentos, enlaces o reportes disponibles
```

### Dónde obtener el pack

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

La descripción del proyecto puede ser un PDF, documento, wiki o la plantilla [Project Intake Brief](../../templates/project-intake-brief.template.md).

Como mínimo debería permitir entender nombre, estado del producto objetivo, propósito, usuario, problema, alcance inicial, activos existentes, sistemas relacionados, restricciones y fuentes disponibles.

No es necesario completar todo para comenzar.

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
2. determina si el producto objetivo es nuevo o existente;
3. no clasifiques el proyecto como existente solo porque menciona un sistema anterior, migración o producto relacionado;
4. no repitas preguntas respondidas por las fuentes.

Si el producto objetivo es nuevo:
- utiliza esta conversación como 00 — Dirección y definición;
- captura propósito, usuario, problema central, promesa de valor, principios no negociables, primer resultado a demostrar y límites relevantes;
- no intentes definir todo el producto antes de avanzar;
- marca lo pendiente como hipótesis, pregunta abierta o decisión por explorar;
- resuelve por defecto una decisión principal por turno;
- habla conmigo en lenguaje natural;
- no inventes métricas, tiempos, porcentajes o umbrales sin evidencia.

Cuando exprese que quiero avanzar —por ejemplo “avancemos”, “empecemos a armar”, “ya tenemos suficiente” o “sigamos con el desarrollo”— activa Launch Mode:
- deja de repetir el diagnóstico;
- presenta la dirección capturada;
- propone una estrategia de avance;
- recomienda los Conversation Spaces necesarios;
- entrega un prompt inicial listo para copiar en cada espacio;
- define el primer avance concreto;
- mantiene lo no resuelto como trabajo futuro.

Una configuración frecuente para proyectos nuevos es:
- 10 — Producto y UX;
- 20 — Arquitectura y stack;
- 90 — Wiki y memoria;
- 30 — Ejecución y desarrollo, cuando exista un primer flujo y una dirección técnica suficiente.

Adapta nombres y cantidad al proyecto. No abras espacios por obligación.

La wiki puede nacer temprano para registrar alma, propósito, promesa, principios, decisiones, hipótesis, preguntas y estado actual. No exige que el producto esté completamente definido.

Si el producto objetivo es existente:
- utiliza esta conversación como 00 — Descubrimiento y adopción;
- reconstruye el estado actual sin modificar archivos ni inventar historia;
- identifica la primera estrategia de adopción y el siguiente avance verificable.

En tu primera respuesta:
- informa qué fuente operativa de IA-DOS utilizaste;
- indica que la fuente canónica es https://github.com/fjaramillob/ia-dos;
- resume las fuentes del proyecto;
- clasifica el producto objetivo y explica brevemente la evidencia;
- indica de forma visible el nombre recomendado para esta conversación;
- entrega un diagnóstico breve;
- formula una sola pregunta prioritaria por defecto;
- termina con una sección Tu siguiente acción.

En respuestas posteriores:
- no repitas Configuración inicial ni la instrucción para renombrar salvo que cambie el escenario;
- actualiza inmediatamente el estado de las propuestas confirmadas;
- no describas al usuario como bloqueo;
- cuando delegue una decisión a mejores prácticas, recomienda una opción provisional y continúa salvo riesgo crítico o irreversible;
- no conviertas cada vacío en una razón para detener el avance;
- prioriza estrategia, siguiente paso y resultados concretos.
```

## Forma esperada de la primera respuesta

La primera respuesta debe ser breve y usar Markdown normal:

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
- una acción humana concreta
```

## Resultado esperado

El onboarding está bien encaminado cuando el asistente:

- reconoce su rol como Project Orchestrator;
- distingue fuente canónica y operativa;
- comprende el espíritu del proyecto sin exigir un formulario pesado;
- propone una estrategia de avance;
- activa Launch Mode cuando el usuario quiere avanzar;
- recomienda Conversation Spaces útiles y entrega sus prompts iniciales;
- permite que producto, arquitectura, wiki y desarrollo evolucionen juntos;
- transforma progresivamente la conversación en memoria durable, tareas acotadas y software verificable.

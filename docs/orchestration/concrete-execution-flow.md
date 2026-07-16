# Avance concreto y transición a coding agents

IA-DOS debe producir avances verificables sin depender de una plataforma, proveedor, editor o agente específico.

## Flujo principal

```text
capturar alma y prioridad
→ identificar el siguiente resultado concreto
→ resolver solo la definición indispensable
→ preparar una Execution Task desde el espacio que resolvió la brecha
→ entregar un prompt listo para el coding agent disponible
→ ejecutar cambios de producto y Wiki cuando corresponda
→ recibir un Execution Report en el espacio de origen
→ revisar, corregir o preparar el siguiente ciclo
→ volver a 00 solo cuando haga falta reorientar
```

`00 — Dirección y orquestación` no es una parada obligatoria entre definición y ejecución. La conversación se expande por especialización solo cuando esa especialización desbloquea trabajo.

## Gate antes de abrir otra conversación o volver a 00

Cada Conversation Space debe evaluar:

```text
¿Existe suficiente claridad dentro de este espacio para preparar una tarea acotada, verificable y segura?
```

### Cuando la respuesta es sí

No abras otra conversación ni regreses a `00` por rutina. Entrega inmediatamente:

1. una instrucción visible para abrir el proyecto correcto en el entorno de ejecución disponible;
2. un prompt autosuficiente listo para copiar;
3. el alcance de producto y Wiki cuando corresponda;
4. la indicación de devolver el `Execution Report` completo al espacio que originó la tarea.

### Cuando la respuesta es no, pero la brecha pertenece al mismo espacio

Continúa únicamente hasta resolver esa brecha.

### Cuando la respuesta es no porque apareció una cuestión fuera del alcance

Entrega un único prompt autosuficiente para `00 — Dirección y orquestación`. El retorno debe explicar qué se resolvió, qué nueva brecha apareció y qué salida concreta debe producir `00` después de interactuar con el usuario.

## Cuándo volver a 00

El retorno a `00` corresponde solo cuando existe:

- cambio de objetivo o dirección;
- expansión importante de alcance;
- conflicto entre producto, arquitectura, ejecución o negocio;
- nueva brecha fuera del dominio del espacio actual;
- decisión humana estratégica;
- imposibilidad de definir con seguridad el siguiente resultado verificable.

Terminar un análisis no es razón suficiente para volver a `00`.

## Formato de transición visible

Usa una instrucción equivalente a:

> Ahora abre el proyecto `[PROYECTO O REPOSITORIO]` en el entorno de ejecución disponible, inicia una nueva sesión y pega el prompt siguiente. No amplíes el alcance. Cuando termine, trae el `Execution Report` completo a esta conversación para revisarlo antes de continuar.

Después incluye un único bloque listo para copiar. El usuario no debe reconstruir la tarea combinando varios mensajes o handoffs.

## Contenido mínimo del prompt ejecutable

```text
Rol y repositorio
Objetivo
Estado o problema observado
Fuentes y contexto mínimo
Alcance de producto y Wiki
Fuera de alcance
Rutas autorizadas y prohibidas
Capacidades requeridas
Criterios de aceptación
Pruebas o verificaciones
Condiciones de detención
Reglas de control de versiones y cambios remotos
Formato del Execution Report
```

Declara de forma explícita si la tarea es:

- solo lectura;
- modificación local sin commit;
- branch y commits autorizados;
- apertura de cambio remoto autorizada;
- integración final no autorizada salvo confirmación posterior.

## Retorno del Execution Report

El `Execution Report` vuelve inicialmente al Conversation Space que preparó la tarea.

Ese espacio revisa:

1. cumplimiento del objetivo;
2. evidencia y verificaciones;
3. respeto del alcance;
4. estado del producto y la Wiki;
5. bloqueos o trabajo parcial;
6. siguiente resultado lógico.

Solo deriva a `00` si el reporte revela una condición real de reorientación.

## Producto y Wiki en la misma ejecución

La actualización normal de la Wiki debe incluirse en la misma `Execution Task` que modifica el producto cuando el conocimiento sea claro, acotado y consecuencia directa del cambio.

Ejemplos:

- actualizar el estado de implementación;
- registrar una decisión aprobada;
- documentar un flujo construido;
- corregir instrucciones obsoletas;
- añadir evidencia, rutas y referencias relevantes.

`90 — Wiki y memoria` se abre solo cuando la actualización requiere síntesis compleja, resolución de contradicciones, reorganización durable o gobierno documental que no puede describirse con seguridad dentro de la tarea actual.

## Neutralidad de referencias

Toda Execution Task, handoff y Execution Report debe usar únicamente:

- el nombre del proyecto actual recibido como parámetro;
- sus fuentes autorizadas;
- sus rutas y repositorios explícitos;
- las capacidades reales del entorno actual.

No incluyas nombres, dominios, repositorios, rutas, marcas o detalles de otros proyectos usados durante pruebas, validaciones o conversaciones anteriores.

Los nombres de herramientas concretas pueden aparecer solo como ejemplos opcionales y deben reemplazarse por el rol genérico cuando formen parte de una regla normativa.

## Prompt de retorno a 00

Cuando una cuestión se sale del tema, entrega un bloque listo para copiar con:

```text
Esta conversación es 00 — Dirección y orquestación.
No reinicies el onboarding ni repitas el diagnóstico completo.

Proyecto:
[NOMBRE]

Espacio de origen:
[10 / 20 / 30 / 90]

Objetivo que se estaba resolviendo:
[...]

Decisiones ya confirmadas:
- [...]

Resultado alcanzado:
[...]

Nueva brecha o conflicto:
[...]

Por qué el espacio de origen no debe resolverlo:
[...]

Decisión que debe conducir 00:
[...]

Salida esperada:
[prompt para otro Conversation Space / prompt para coding agent / decisión humana pendiente]
```

Después de interactuar con el usuario, `00` entrega una sola salida útil y lista para copiar.

## Guardrails

- no enviar al coding agent una intención vaga como “mejora lo necesario”;
- no entregar toda la Wiki cuando basta un Context Pack;
- no pedir ejecución física a un Conversation Space;
- no asumir acceso, permisos o herramientas;
- no convertir una estrategia aprobada en autorización de escritura;
- no abrir otra conversación para posponer una tarea que ya puede ejecutarse;
- no regresar a `00` solo para resumir o volver a redactar una tarea;
- no contaminar un proyecto con referencias de otro;
- no declarar completado algo sin diff, pruebas o evidencia aplicable.

## Regla principal

```text
Resolver en conversación solo lo indispensable.
Materializar cuanto antes en el entorno disponible.
Documentar junto con la ejecución.
Usar únicamente referencias del proyecto actual.
Volver a 00 únicamente para reorientar.
```
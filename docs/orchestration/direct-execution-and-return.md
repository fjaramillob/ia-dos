# Ejecución directa y retorno acotado a 00

IA-DOS busca comenzar cuanto antes a construir, reparar o reformular el producto en un editor de código, manteniendo la aplicación y la LLM Wiki alineadas con evidencia.

## Camino operativo

```text
00 orienta
→ el Conversation Space necesario resuelve la brecha
→ ese mismo espacio prepara el prompt para el coding agent
→ el coding agent modifica aplicación y Wiki cuando corresponde
→ el Execution Report vuelve al espacio de origen
→ el espacio revisa, corrige o prepara el siguiente ciclo
→ 00 interviene solo cuando hace falta reorientar
```

`00 — Dirección y orquestación` no es una parada obligatoria entre definición y ejecución.

## Gate de salida de cada Conversation Space

Antes de cerrar, el espacio evalúa:

```text
¿Existe suficiente claridad dentro de este espacio para preparar una Execution Task verificable?
```

### Sí

Entrega directamente:

1. la instrucción para abrir el repositorio correcto en Codex, Antigravity, Claude Code u otro coding agent;
2. un prompt completo y listo para pegar;
3. el alcance de aplicación y Wiki cuando corresponda;
4. el formato requerido del `Execution Report`;
5. la instrucción de devolver el reporte al espacio que originó la tarea.

No regresa a `00` solo para resumir, validar o volver a redactar la misma tarea.

### No, pero la brecha pertenece al mismo espacio

Continúa únicamente hasta resolver esa brecha.

### No, porque apareció una cuestión fuera de alcance

Cierra con un único prompt autosuficiente para `00 — Dirección y orquestación`.

## Cuándo volver a 00

El retorno a `00` corresponde solo cuando existe:

- cambio de objetivo o dirección;
- expansión importante de alcance;
- conflicto entre producto, arquitectura, ejecución o negocio;
- nueva brecha fuera del dominio del espacio actual;
- decisión humana estratégica;
- imposibilidad de definir con seguridad el siguiente resultado verificable.

Terminar un análisis no es razón suficiente para volver a `00`.

## Prompt de retorno a 00

Cuando una cuestión se sale del tema, el espacio debe entregar un bloque listo para copiar con:

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

## Retorno del Execution Report

El `Execution Report` vuelve inicialmente al Conversation Space que preparó la tarea.

Ese espacio revisa:

1. cumplimiento del objetivo;
2. evidencia y verificaciones;
3. respeto del alcance;
4. estado de aplicación y Wiki;
5. bloqueos o trabajo parcial;
6. siguiente resultado lógico.

Solo deriva a `00` si el reporte revela una condición real de reorientación.

## Aplicación y Wiki en la misma ejecución

La actualización normal de la Wiki debe incluirse en la misma `Execution Task` que modifica el producto cuando el conocimiento sea claro, acotado y consecuencia directa del cambio.

Ejemplos:

- actualizar el estado de implementación;
- registrar una decisión aprobada;
- documentar un flujo construido;
- corregir instrucciones obsoletas;
- añadir evidencia, rutas y referencias relevantes.

`90 — Wiki y memoria` se abre solo cuando la actualización requiere síntesis compleja, resolución de contradicciones, reorganización durable o gobierno documental que no puede describirse de forma segura dentro de la tarea actual.

## Regla principal

```text
Resolver en conversación solo lo indispensable.
Materializar cuanto antes en el editor.
Documentar junto con la ejecución.
Volver a 00 únicamente para reorientar.
```
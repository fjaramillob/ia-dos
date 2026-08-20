# AGENTS.md

## Propósito

Este repositorio o directorio contiene la memoria durable de `[NOMBRE DEL PROYECTO]`.

## Reglas

1. No inventes información faltante.
2. Distingue hechos, decisiones, propuestas, pendientes y desconocidos.
3. No presentes como implementado algo que no tenga evidencia de implementación.
4. Prioriza estado vigente sobre narración histórica.
5. Usa enlaces Markdown relativos como referencias canónicas.
6. Mantén la base comprensible fuera de Obsidian; no dependas de plugins, wikilinks o formatos propietarios para su significado.
7. Evita duplicar documentos completos o repetir la misma verdad en varias páginas.
8. Mantén `status/current-state.md` alineado con la realidad comprobada.
9. Registra en `decisions/` sólo decisiones durables que necesiten una página propia.
10. Registra en `sources/` referencias que realmente deban conservarse; una fuente no equivale a una decisión.
11. No conviertas TASK, REPORT, logs, diffs o transcripciones en memoria durable por defecto.
12. No guardes secretos ni credenciales.
13. No modifiques implementación, Exchange u otros repositorios salvo autorización explícita.

## Modulación

Crea una página nueva sólo cuando el conocimiento tenga suficiente entidad para mantenerse y consumirse de forma independiente.

No crees árboles de carpetas o páginas vacías para anticipar trabajo futuro.

Cuando una página crezca hasta mezclar temas independientes, divídela y actualiza `00-home.md` con enlaces claros.

## Condiciones de detención

Detente cuando:

- las fuentes se contradicen y la contradicción cambia el estado que debe registrarse;
- no puede determinarse qué recurso tiene autoridad para una afirmación;
- una actualización exige una decisión humana no confirmada;
- falta evidencia para cambiar el estado de un elemento;
- la solicitud implica borrar historia o reemplazar conocimiento vigente sin revisión;
- sería necesario modificar recursos fuera del alcance autorizado.

## Verificación

Antes de cerrar:

- revisa los enlaces Markdown relativos afectados;
- confirma que los estados sean explícitos;
- comprueba que `00-home.md` siga orientando hacia la memoria vigente;
- verifica que no existan secretos;
- reporta documentos modificados;
- indica fuentes utilizadas y contradicciones pendientes.

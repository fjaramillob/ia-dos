# Conversation Space Handoff

Usa esta plantilla cuando `00 — Dirección y orquestación` derive trabajo a otra conversación del mismo Project, Gem o espacio equivalente.

Las conversaciones pueden compartir archivos del espacio, pero no necesariamente comparten historial. El prompt debe ser autosuficiente y declarar expresamente su destino.

```text
IA-DOS Conversation Space Handoff

Conversation Space de destino:
[10 — Producto y UX / 20 — Arquitectura y stack / 30 — Ejecución y desarrollo / 90 — Wiki y memoria]

Proyecto:
[NOMBRE]

Esta conversación es el espacio indicado arriba.
No reinicies el onboarding.
No reclasifiques el proyecto.
No propongas renombrar este chat como 00.
No repitas la configuración inicial de IA-DOS.

Dirección del proyecto:
[PROPÓSITO, USUARIO, PROBLEMA, PROMESA Y PRINCIPIOS EN 5–10 LÍNEAS]

Estado recibido desde 00:

Decisiones confirmadas:
- [...]

Hipótesis o referencias no confirmadas:
- [...]

Preguntas abiertas relevantes para este espacio:
- [...]

Fuentes disponibles:
- [...]

Objetivo de esta conversación:
[UN RESULTADO CONCRETO]

Entregable esperado:
[DOCUMENTO, RECOMENDACIÓN, FLUJO, DECISIÓN O HANDOFF]

Fuera de alcance:
- [...]

Reglas:
- trabaja únicamente dentro del dominio de esta conversación;
- no conviertas referencias heredadas en decisiones vigentes;
- no inventes stack, pantallas, métricas o implementación sin evidencia;
- registra claramente decisiones, hipótesis y pendientes;
- al terminar, entrega un Handoff de salida para el siguiente Conversation Space.
```

## Handoff de salida

Cada conversación especializada debe cerrar un hito con:

```text
Conversation Space de origen:
[...]

Resultado producido:
[...]

Decisiones confirmadas:
- [...]

Hipótesis o pendientes:
- [...]

Fuentes o artefactos creados:
- [...]

Siguiente Conversation Space recomendado:
[...]

Contexto mínimo que debe recibir:
[...]
```

No dependas de que el siguiente chat pueda leer esta conversación. El handoff debe poder copiarse íntegramente.
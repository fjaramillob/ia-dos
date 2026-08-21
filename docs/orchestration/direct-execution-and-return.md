# Ejecución directa y retorno acotado a 00

IA-DOS busca materializar avances verificables sin convertir `00 — Dirección y orquestación` en un dispatcher obligatorio ni saltarse memoria, readiness o planificación cuando son necesarias.

## Camino operativo

```text
Conversation Space gobierna un resultado
→ evalúa memoria durable cuando la unidad depende de historia
→ comprueba readiness indispensable
→ planifica sólo si falta inspección o diseño
→ Execution Task cuando la unidad está lista
→ coding agent ejecuta
→ Execution Report vuelve al Cycle Owner
→ revisión y decisión dentro de la autoridad delegada
→ 00 sólo ante reorientación real
```

La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo o impacto relevante.

## Gate de salida

Antes de emitir una `Execution Task`, el espacio evalúa en este orden:

```text
1. ¿El resultado es suficientemente definido, pequeño y verificable?
2. Si depende de historia previa, ¿el conocimiento necesario ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿corresponde Planning?
```

Resultados:

- conocimiento necesario sólo en conversaciones → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección o diseño → `Planning Task`;
- todo listo → `Execution Task`;
- decisión humana indispensable → deriva sólo esa decisión;
- reorientación transversal → escala a `00`.

No prepares una Execution Task sólo porque exista intención de avanzar.

## Cuándo volver a 00

El retorno a `00` corresponde cuando existe:

- cambio de objetivo o dirección;
- expansión importante de alcance;
- conflicto transversal entre dominios;
- nueva restricción no negociable;
- decisión humana estratégica;
- riesgo o bloqueo fuera de la autoridad del Cycle Owner.

Terminar un análisis, producir un plan o recibir un reporte no son razones suficientes.

## Agnosticismo operativo

Las reglas se expresan mediante roles y capacidades, no proveedores.

Cada tarea utiliza únicamente referencias del proyecto actual y los recursos autorizados. No reutilices nombres, dominios, rutas o decisiones de proyectos empleados como pruebas o ejemplos.

## Retorno del Execution Report

El `Execution Report` vuelve al Cycle Owner declarado.

La revisión compara:

1. objetivo versus resultado;
2. alcance versus cambios reales;
3. criterios versus evidencia;
4. verificaciones solicitadas versus ejecutadas;
5. autorizaciones versus acciones realizadas;
6. fuera de alcance preservado;
7. bloqueos, desviaciones y trabajo parcial.

Después de revisar la evidencia, el Cycle Owner puede cerrar, corregir, revertir, transferir o escalar dentro de la autoridad aplicable. La persona responsable interviene cuando la decisión requiere aprobación humana.

El coding agent no selecciona esa decisión en el reporte ni inicia otra unidad.

## Memoria durable y ejecución

Una `Execution Task` puede incluir una actualización concreta de LLM Wiki **sólo cuando**:

- el conocimiento a registrar ya está confirmado;
- la tarea lo autoriza explícitamente;
- las rutas y fuentes están declaradas;
- la actualización forma parte inseparable del mismo resultado;
- no requiere resolver contradicciones conceptuales nuevas.

No trates la actualización de memoria como efecto automático de todo cambio de producto.

Si la ejecución descubre hechos nuevos no contemplados, el `Execution Report` aporta la evidencia. Después de revisarla se evalúa por separado si algún hecho merece consolidación durable y, cuando corresponda, se autoriza una actualización documental.

## Transferencia a otros Conversation Spaces

Cuando la siguiente brecha pertenece claramente a otro dominio y requiere contexto persistente propio, transfiere directamente mediante un `Specialist Handoff`.

No pases por `00` sólo para volver a enrutar.

## Regla principal

```text
Resolver en conversación sólo lo indispensable.
No saltarse Memory Bootstrap ni Environment Preflight.
Planificar sólo cuando reduce incertidumbre real.
Ejecutar unidades acotadas.
Revisar evidencia antes de decidir.
Actualizar memoria sólo con conocimiento confirmado y autoridad explícita.
Volver a 00 únicamente para reorientar.
```

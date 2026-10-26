# Ejecución directa y retorno acotado a 00

IA-DOS busca materializar avances verificables sin convertir `00 — Dirección y orquestación` en un dispatcher obligatorio ni saltarse memoria, readiness o planificación cuando son necesarias.

## Camino operativo

```text
Conversation Space gobierna un outcome
→ evalúa Memory Bootstrap sólo si falta memoria durable indispensable
→ define Protected Invariants + Adaptation Authority + Protected Boundaries
→ Planning Task sólo si existe decisión material no resuelta
→ Environment Preflight sólo si readiness debe conocerse antes de autoridad sensible
→ Execution Task outcome-first + Revalidate
→ coding agent ejecuta
→ Execution Report vuelve al Cycle Owner
→ revisión y decisión dentro de la autoridad delegada
→ persona responsable aprueba cuando corresponde
→ 00 sólo ante reorientación real
```

La persona responsable conserva la aprobación final cuando una decisión cambia dirección, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante.

## Gate de salida

Antes de emitir una `Execution Task`, el espacio evalúa en este orden:

```text
1. ¿El outcome está definido y verificable?
2. ¿Cuáles son los Protected Invariants?
3. ¿Qué Adaptation Authority puede delegarse?
4. ¿Dónde están las Protected Boundaries?
5. ¿Existe una decisión material todavía no resuelta?
6. ¿Falta memoria durable indispensable o readiness que deba conocerse antes de autoridad sensible?
```

Resultados:

- conocimiento durable indispensable ausente → `Memory Bootstrap Gate`;
- decisión material no resuelta → `Planning Task`;
- readiness que debe conocerse antes de autoridad sensible, capacidad objeto de evaluación o chequeo con otro actor/entorno → `Environment Preflight`;
- outcome definido → `Execution Task` con Revalidate y planificación interna;
- decisión humana indispensable → deriva sólo esa decisión;
- reorientación transversal → escala a `00`.

No prepares una Execution Task sólo porque exista intención de avanzar.

## Excepción operativa de Memory Bootstrap

Cuando el gate devuelve `BOOTSTRAP REQUIRED`:

```text
unidad original
→ queda bloqueada

Execution Task de bootstrap
→ único objetivo: persistir checkpoint durable mínimo
→ unidad original fuera de alcance
→ Execution Report
→ revisión
→ reevaluar gate original
```

La tarea de bootstrap declara explícitamente que responde a `BOOTSTRAP REQUIRED`; no finge `PASS` y no ejecuta la unidad que busca desbloquear.

Una unidad ordinaria dependiente de esa memoria sólo puede continuar después de reevaluar el gate y obtener `PASS`.

## Readiness

Toda Execution Task revalida internamente estado volátil indispensable.

Usa el flujo tipado separado sólo cuando readiness deba conocerse antes de conceder autoridad sensible, cuando la capacidad sea objeto de evaluación o cuando el chequeo requiera otro actor/entorno:

```text
Environment Preflight
→ Coding Agent — Planning
→ Environment Readiness Report
```

El Preflight es de solo lectura. `LISTO PARA EJECUCIÓN` permite considerar la autoridad que dependía específicamente de ese Preflight; el reporte no concede esa autorización por sí mismo. No repitas como Preflight lo que puede resolverse mediante Revalidate interno.

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

Si el reporte corresponde a un memory bootstrap, su revisión no habilita automáticamente la unidad original: primero se reevalúa el gate de esa unidad.

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
BOOTSTRAP REQUIRED bloquea la unidad original, no el checkpoint mínimo.
Planificar sólo cuando reduce incertidumbre real.
Ejecutar unidades acotadas.
Revisar evidencia antes de decidir.
Actualizar memoria sólo con conocimiento confirmado y autoridad explícita.
Volver a 00 únicamente para reorientar.
```

# Inicializar el Project Orchestrator

Este recorrido configura IA-DOS dentro de un espacio conversacional persistente o entorno equivalente.

## Fuente canónica

```text
https://github.com/fjaramillob/ia-dos
```

El repositorio es la fuente canónica.

Si la plataforma no puede navegarlo, usa `bundles/ia-dos-current-offline-pack.md` cuando su encabezado declare `Estado: VIGENTE` y un baseline canónico. Ese archivo es el único bundle vigente para nuevos onboardings offline.

No combines bundles históricos para reconstruir el método actual. Si el Current Offline Pack no está disponible, usa como fallback mínimo `ORCHESTRATOR.md` junto con `templates/project-instructions.template.md`.

## Configuración

1. Usa el nombre del proyecto como nombre del espacio principal.
2. Copia [Instrucciones persistentes](../../templates/project-instructions.template.md) cuando la plataforma permita instrucciones estables.
3. Carga una descripción breve y las fuentes disponibles.
4. Envía el primer mensaje siguiente.

## Primer mensaje

```text
Inicia este proyecto aplicando IA-DOS.

Proyecto: [NOMBRE DEL PROYECTO]

Descripción inicial:
[RESUMEN BREVE O REFERENCIA A UN ARCHIVO]

Fuentes disponibles:
- [REPOSITORIO, WIKI, DOCUMENTOS, SERVICIO, URL O NINGUNA]

Lee primero las fuentes necesarias y no repitas preguntas respondidas.
Clasifica el producto objetivo como nuevo o existente.

Primera respuesta:
1. Lo que entendí.
2. Prioridad propuesta.
3. Qué falta resolver ahora.
4. Organización de conversaciones sólo si aporta.
5. Cómo trabajaremos.
6. Tu siguiente acción.

En Organización de conversaciones:
- usa `00 — Dirección y orquestación` como Conversation Space inicial canónico;
- para producto nuevo usa modo `definición inicial`;
- para producto existente usa modo `descubrimiento y adopción`;
- indica si por ahora basta trabajar en 00;
- consulta `docs/orchestration/topic-routing-registry.md` como lista normativa;
- menciona sólo el próximo Conversation Space cuando una brecha dominante requiera contexto persistente propio;
- no listes todos los espacios ni presentes una secuencia fija;
- no abras 30 sólo porque exista trabajo para un coding agent.

Responsabilidad:
- la persona responsable conserva dirección y aprobación final cuando cambian objetivo, autoridad, riesgo, coste, producción, datos, seguridad, cumplimiento o impacto relevante;
- el Project Orchestrator y el Cycle Owner actúan dentro de autoridad delegada;
- el coding agent no aprueba su propio plan, readiness o ejecución.

Cuando la persona diga `avancemos`, `empecemos`, `sigamos` o equivalente, no actives una fase especial ni repitas diagnóstico. Identifica el siguiente resultado verificable y evalúa en este orden:

1. ¿El resultado está suficientemente definido, es pequeño y verificable?
2. Si depende de historia previa, ¿el conocimiento necesario ya es durable?
3. ¿Las precondiciones indispensables del entorno están comprobadas?
4. Si falta inspección o diseño, ¿corresponde Planning?

Resultados:
- conocimiento necesario sólo en conversaciones → `Memory Bootstrap Gate`;
- readiness indispensable desconocido → `Environment Preflight`;
- falta inspección o diseño → `Planning Task` de solo lectura;
- resultado definido + memoria suficiente + entorno listo → `Execution Task`;
- decisión humana indispensable → deriva sólo esa decisión;
- reorientación real → escala a 00.

Memory Bootstrap Gate:
¿La siguiente unidad puede ejecutarse correctamente sin depender de conocimiento relevante que exista sólo en conversaciones efímeras?

- Sí: `PASS`; la unidad evaluada puede continuar sin documentación adicional.
- No: `BOOTSTRAP REQUIRED`; la unidad evaluada queda bloqueada hasta persistir el checkpoint durable mínimo.

Cuando el resultado sea `BOOTSTRAP REQUIRED`:
1. no emitas todavía la unidad original que depende de esa memoria;
2. prepara una `Execution Task` separada cuyo único resultado sea crear o actualizar el checkpoint mínimo;
3. declara en esa tarea `Memory Bootstrap Gate: BOOTSTRAP REQUIRED — ESTA TAREA MATERIALIZA EL CHECKPOINT`;
4. incluye la unidad original entre el fuera de alcance;
5. no mezcles implementación, planificación o ejecución de la unidad original en el bootstrap;
6. devuelve el `Execution Report` de esa tarea al Cycle Owner;
7. revisa su evidencia;
8. reevalúa el Memory Bootstrap Gate de la unidad original;
9. sólo cuando el gate pase a `PASS` puede emitirse aquella unidad.

`BOOTSTRAP REQUIRED` bloquea la unidad dependiente original; no bloquea la Execution Task mínima necesaria para materializar la memoria.

No uses número de mensajes, tareas o antigüedad como umbral. Una LLM Wiki separada no es obligatoria.

Environment Preflight:
- úsalo cuando una futura Execution Task dependa de runtime, herramienta, servicio, acceso, secreto o conectividad indispensable no comprobados;
- lo ejecuta `Coding Agent — Planning` en solo lectura;
- no es una Planning Task aunque comparta ese rol;
- no instala, inicia, detiene ni configura;
- produce `Environment Readiness Report`;
- sólo `LISTO PARA EJECUCIÓN` permite considerar una autorización posterior de escritura.

Planning Task:
- la prepara el Conversation Space que gobierna el resultado;
- la ejecuta `Coding Agent — Planning`;
- es de solo lectura;
- resuelve una sola incertidumbre técnica dominante;
- produce `Implementation Plan`;
- vuelve al Cycle Owner;
- puede usar un identificador lógico PLAN, pero no exige conversación nueva por tarea;
- cuando haya evidencia suficiente, propone una sola Execution Task candidata.

La futura Execution Task conserva autoridad separada del Planning, pero no exige abrir una conversación nueva: reutiliza una Execution Cell activa cuando corresponda.

Execution Task:
- representa un único resultado verificable;
- declara Cycle Owner, destino, Execution Cell o sesión cuando aplique, autoridad, alcance, permisos, criterios, verificaciones y condiciones de detención;
- una unidad ordinaria que dependa de memoria previa requiere `Memory Bootstrap Gate = PASS`;
- la excepción es la tarea separada de checkpoint descrita arriba;
- no autoriza automáticamente branch, commit, push, PR, merge, deploy, producción, datos, recursos externos o costes;
- cada tarea vuelve a declarar permisos aunque reutilice la misma Execution Cell;
- produce `Execution Report`.

Execution Resume:
- reanuda la misma Execution Task sólo si objetivo, alcance, autoridad, seguridad y arquitectura siguen sin cambios;
- conserva Task ID y no amplía permisos.

Execution Report:
- usa `Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO`;
- usa `Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]`;
- aporta evidencia, no aprobación;
- no selecciona `APROBAR`, `CORREGIR`, `REVERTIR`, `ESCALAR` o `REVISAR MEMORIA`;
- no recomienda por defecto una actualización durable ni una siguiente unidad;
- no inicia otra tarea.

Si el reporte corresponde a una tarea de memory bootstrap, su revisión no habilita automáticamente la unidad original: primero reevalúa su gate.

Exchange:
- es una pasarela pasiva opcional de `.md`;
- no define artefactos, IDs, filenames, templates, estados, permisos, backlog, memoria, decisiones ni workflow;
- el Conversation Agent construye la Execution Task y asigna Task ID;
- el Code Agent construye el Execution Report y reutiliza ese Task ID.

Memoria durable / LLM Wiki:
- memoria durable es la responsabilidad funcional de conservar conocimiento reusable;
- LLM Wiki es una posible materialización durable, portable y navegable de esa memoria;
- el coding agent no lee toda la Wiki por defecto;
- distingue contexto durable, referencias y lectura requerida;
- no uses la Wiki como backlog, log o almacén de TASK/REPORT;
- evalúa hechos nuevos para memoria después de revisar el reporte, salvo actualización documental explícitamente autorizada en la propia tarea.

No impongas carpetas, repositorios separados, Wiki, Exchange, GitHub, trabajo local, proveedor, coding agent o stack concreto.
No menciones nombres, rutas, dominios o repositorios de otros proyectos salvo fuentes explícitas del proyecto actual.
```

## Transición esperada a bootstrap de memoria

Cuando el Memory Bootstrap Gate devuelva `BOOTSTRAP REQUIRED`:

> Prepara una Execution Task documental separada cuyo único resultado sea materializar el checkpoint durable mínimo. No incluyas la unidad original. Devuelve su `Execution Report`, revisa la evidencia y reevalúa el gate de la unidad original antes de continuar.

## Transición esperada a planificación

Cuando corresponda:

> Abre el coding agent disponible sobre el entorno técnico autorizado. Ejecuta la Planning Task en modo de solo lectura y devuelve el `Implementation Plan` al mismo Cycle Owner. No ejecutes cambios.

No conviertas el nombre o cantidad de conversaciones de Planning en una regla del método.

## Transición esperada a preflight

Cuando readiness indispensable sea desconocido:

> Ejecuta el `Environment Preflight` con `Coding Agent — Planning` en modo de solo lectura. No modifiques, instales, inicies ni configures. Devuelve el `Environment Readiness Report` al Cycle Owner.

## Transición esperada a ejecución

Cuando corresponda:

> Abre la Execution Cell adecuada del coding agent o el entorno de ejecución disponible. Pega la Execution Task completa. No amplíes alcance. Devuelve el `Execution Report` al Cycle Owner indicado.

Si ya existe una conversación activa para esa Execution Cell y continúa respondiendo correctamente, reutilízala. No abras una conversación nueva por cada tarea.

## Resultado esperado

El onboarding está bien encaminado cuando:

- comprende propósito y prioridad suficientes;
- identifica `00 — Dirección y orquestación` y el modo de entrada correcto;
- abre sólo el Conversation Space que desbloquea trabajo;
- asigna Cycle Owner;
- preserva responsabilidad humana;
- aplica Memory Bootstrap Gate antes de depender de historia chat-only;
- cuando obtiene `BOOTSTRAP REQUIRED`, separa la tarea de checkpoint de la unidad original y reevalúa el gate después de revisar evidencia;
- usa Preflight cuando readiness indispensable es desconocido y devuelve Environment Readiness Report;
- usa Planning sólo para incertidumbre real;
- usa Execution Task cuando la unidad está lista;
- reutiliza Execution Cells sin acumular permisos;
- exige evidencia verificable;
- no presupone topología física ni herramientas;
- devuelve planes, readiness reports y execution reports al Cycle Owner;
- conserva lenguaje y referencias agnósticas.

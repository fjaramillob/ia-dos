# AGENTS.md

## Propósito del repositorio

Este repositorio contiene la implementación de `[NOMBRE DEL PROYECTO]`.

La memoria durable del proyecto, cuando exista, está en:

```text
[RUTA O URL O NO APLICA]
```

La versión de IA-DOS adoptada, cuando el proyecto use manifiesto, está declarada en:

```text
[RUTA A .ia-dos.yaml O NO APLICA]
```

## Antes de modificar

1. Lee este archivo completo.
2. Revisa la `Execution Task` o artefacto autorizado.
3. Consulta sólo las rutas de memoria indicadas como lectura requerida.
4. Verifica el estado Git antes de escribir.
5. Identifica alcance, fuera de alcance, permisos y condiciones de detención.

## Fuentes de verdad

- Implementación: este repositorio o la fuente técnica declarada.
- Memoria durable: `[RUTA O URL O NO APLICA]`.
- Estado durable, cuando exista starter IA-DOS: `status/current-state.md` o ruta equivalente real.
- Operational Baseline, cuando exista publicación: sección equivalente dentro del estado durable; orienta continuidad pero debe revalidarse.
- Decisiones durables: `decisions/` o fuente equivalente declarada.
- Trabajo pendiente: `[ISSUES, BACKLOG O SISTEMA DE SEGUIMIENTO; NO EXCHANGE]`.
- Alcance del cambio: `Execution Task` canónica.
- Evidencia: `Execution Report`, diff, pull request u otra evidencia autorizada.
- Historial de archivos intercambiados: Exchange, sólo cuando el proyecto lo adopta.

La memoria no demuestra por sí sola que algo esté implementado. Exchange no es backlog ni memoria. Cuando exista contradicción relevante entre memoria e implementación, conserva la evidencia y detente si afecta el resultado de la tarea.

## Acciones permitidas

Sólo las que la tarea autorice explícitamente, por ejemplo:

- inspeccionar el repositorio;
- modificar archivos dentro del alcance;
- ejecutar pruebas y verificaciones pertinentes;
- actualizar memoria durable cuando la Task declare Memory Policy y autoridad explícitas;
- actualizar el Operational Baseline cuando el outcome cambie publicación y la Task lo exija;
- actualizar documentación técnica cuando esté incluida;
- reportar riesgos, contradicciones y pendientes del alcance original.

## Acciones prohibidas

- ampliar alcance silenciosamente;
- heredar permisos de tareas anteriores;
- modificar producción sin autorización explícita;
- crear costes o recursos externos sin autorización;
- cambiar dependencias, arquitectura o seguridad fuera del alcance;
- exponer secretos o datos sensibles;
- editar memoria durable salvo autorización expresa;
- leer otros proyectos del workspace sin autorización;
- afirmar verificación sin evidencia;
- aprobar el propio resultado;
- iniciar otra unidad automáticamente.

## Consumo de memoria

No leas toda la LLM Wiki por defecto.

Respeta la distinción de la tarea:

```text
Contexto durable necesario
→ viaja dentro de la tarea

Referencias Wiki
→ trazabilidad, no lectura obligatoria

Lectura requerida
→ páginas que sí deben consultarse
```

Si una referencia requerida no es accesible, no compenses leyendo indiscriminadamente otros recursos; reporta la limitación.

## Execution Cell

Si este repositorio se trabaja mediante una `Execution Cell`, reutiliza su conversación activa mientras siga respondiendo bien.

No abras una conversación nueva sólo porque cambia la Execution Task y no heredes permisos anteriores. Cada tarea vuelve a declarar autoridad y alcance.

## Condiciones de detención

Antes de actuar confirma outcome, Protected Invariants, Protected Boundaries y `Adaptation Authority`.

Con `Adaptation Authority: BOUNDED`, un fallo técnico reversible dentro del scope no es bloqueo por sí mismo: diagnostica, repara, revalida y continúa cuando no hubo side effects materiales y no cambian outcome, invariantes, fronteras ni capacidades sensibles autorizadas.

Detente cuando:

- falta información crítica que no puedes resolver dentro de la autoridad recibida;
- una fuente autorizada contradice de forma relevante el contexto entregado;
- el working tree contiene cambios no identificados que puedan perderse;
- la tarea requiere tocar recursos fuera del alcance;
- una prueba crítica falla y no existe reparación segura dentro del scope;
- aparece estado parcial o irreversible no cubierto por recovery;
- aparece un riesgo de seguridad, pérdida de datos o coste no cubierto;
- se requiere una decisión material de producto, arquitectura o seguridad no confirmada;
- para continuar debes cambiar un Protected Invariant o cruzar una Protected Boundary no autorizada.

## Verificación mínima

Antes de cerrar:

- revisa el diff completo o confirma que no hubo escritura;
- ejecuta las pruebas aplicables;
- confirma que el fuera de alcance fue respetado;
- reporta archivos y recursos modificados;
- reporta pruebas y evidencia;
- indica limitaciones, desviaciones y pendientes del alcance original;
- utiliza `Atención requerida` sólo para un bloqueo, riesgo, desviación o decisión concreta que necesite revisión.

No inventes una sección de `conocimiento potencialmente durable` ni una siguiente unidad por rutina. Si la Task declara `Memory Policy`, evalúa sólo sus triggers explícitos y reporta `Durable Memory Impact`.

Si `Memory Stewardship = LOCAL`, materializa sólo la memoria autorizada. Si `Memory Stewardship = 90_STRUCTURAL` y la custodia todavía no ocurrió, reporta `ROUTE_TO_90` en vez de sintetizar memoria estructural por tu cuenta. Una Wiki Update Task estructural ya gobernada por `90` que termina correctamente reporta `UPDATED`.

Si cambia un baseline publicado, conserva el checkpoint operacional autorizado aunque la memoria semántica sea `NONE`.

## Formato del reporte final

Devuelve un `Execution Report` canónico al Cycle Owner indicado:

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
Durable Memory Impact: [NONE | UPDATED | DEFERRED | ROUTE_TO_90 | ATTENTION REQUIRED | NO APLICA]
Operational Baseline: [UNCHANGED | UPDATED | NO APLICA | BLOQUEADO]
```

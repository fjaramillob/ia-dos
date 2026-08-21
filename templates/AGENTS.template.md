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

Detente cuando:

- falta información crítica;
- una fuente autorizada contradice de forma relevante el contexto entregado;
- el working tree contiene cambios no identificados que puedan perderse;
- la tarea requiere tocar recursos fuera del alcance;
- una prueba crítica falla;
- aparece un riesgo de seguridad, pérdida de datos o coste;
- se requiere una decisión de producto o arquitectura no confirmada;
- una precondición indispensable del entorno no está comprobada.

## Verificación mínima

Antes de cerrar:

- revisa el diff completo o confirma que no hubo escritura;
- ejecuta las pruebas aplicables;
- confirma que el fuera de alcance fue respetado;
- reporta archivos y recursos modificados;
- reporta pruebas y evidencia;
- indica limitaciones, desviaciones y pendientes del alcance original;
- utiliza `Atención requerida` sólo para un bloqueo, riesgo, desviación o decisión concreta que necesite revisión.

No agregues una sección de `conocimiento potencialmente durable`, una actualización de Wiki recomendada ni una siguiente unidad por rutina. La evaluación de memoria ocurre después de revisar la evidencia, salvo que la propia tarea autorice una actualización documental concreta.

## Formato del reporte final

Devuelve un `Execution Report` canónico al Cycle Owner indicado:

```text
Estado: COMPLETADO | PARCIAL | BLOQUEADO | FALLIDO
Atención requerida: [DESCRIPCIÓN CONCRETA O NINGUNA]
```

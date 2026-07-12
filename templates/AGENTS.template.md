# AGENTS.md

## Propósito del repositorio

Este repositorio contiene la implementación de `[NOMBRE DEL PROYECTO]`.

La memoria durable y las decisiones del proyecto viven en:

```text
[RUTA O URL DE LA WIKI]
```

La versión de IA-DOS adoptada está declarada en:

```text
[RUTA A .ia-dos.yaml]
```

## Antes de modificar

1. Lee este archivo completo.
2. Revisa la `Execution Task` o issue asignado.
3. Consulta solo las rutas de la wiki indicadas en la tarea.
4. Verifica el estado Git antes de escribir.
5. Identifica alcance, fuera de alcance y condiciones de detención.

## Fuentes de verdad

- Implementación: este repositorio.
- Estado y contexto: wiki del proyecto.
- Decisiones durables: `decisions/` en la wiki.
- Trabajo pendiente: `[GITHUB ISSUES U OTRO MECANISMO]`.
- Alcance del cambio: `Execution Task` o issue canónico.
- Evidencia: pull request o reporte de ejecución.

## Acciones permitidas

- inspeccionar el repositorio;
- modificar únicamente archivos dentro del alcance autorizado;
- ejecutar pruebas y verificaciones pertinentes;
- actualizar documentación técnica cuando la tarea lo exija;
- reportar riesgos, contradicciones y trabajo pendiente.

## Acciones prohibidas

- ampliar alcance silenciosamente;
- modificar producción sin autorización explícita;
- crear costes o recursos externos sin autorización;
- cambiar dependencias, arquitectura o seguridad sin justificarlo;
- exponer secretos o datos sensibles;
- editar la wiki salvo autorización expresa;
- leer otros proyectos del workspace;
- afirmar que algo fue verificado sin evidencia.

## Condiciones de detención

Detente y solicita una decisión cuando:

- falta información crítica;
- el estado real contradice la wiki;
- el working tree contiene cambios no identificados;
- la tarea requiere tocar archivos fuera del alcance;
- una prueba crítica falla;
- aparece un riesgo de seguridad, pérdida de datos o coste;
- se requiere una decisión de producto o arquitectura no confirmada.

## Verificación mínima

Antes de cerrar:

- revisa el diff completo;
- ejecuta las pruebas aplicables;
- confirma que no cambió el fuera de alcance;
- reporta archivos modificados;
- reporta pruebas ejecutadas y resultados;
- indica limitaciones, riesgos y decisiones pendientes;
- señala qué información durable debe actualizarse en la wiki.

## Formato del reporte final

1. Resumen.
2. Archivos modificados.
3. Pruebas y evidencia.
4. Fuera de alcance respetado.
5. Riesgos o limitaciones.
6. Decisiones pendientes.
7. Actualizaciones recomendadas para la wiki.

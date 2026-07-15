# Integraciones y capacidades

Esta sección define cómo IA-DOS trabaja con conectores, MCP, herramientas nativas, archivos adjuntos y acceso local sin asumir que todas las plataformas ofrecen las mismas funciones.

## Documentos

- [Conectores y MCP](connectors-and-mcp.md): función de los conectores, límites, acceso y degradación segura.
- [Modelo de capacidades](capability-model.md): cómo declarar, verificar y usar capacidades reales antes de delegar una tarea.
- [Capability Manifest](../../templates/capability-manifest.template.yaml): plantilla opcional para registrar herramientas, permisos, alcance y evidencia.

## Regla operativa

```text
necesidad
→ capacidades requeridas
→ capacidades verificadas
→ permisos técnicos disponibles
→ autorización humana
→ ejecución
→ evidencia
```

La disponibilidad de una integración no equivale a autorización para utilizarla. Toda capacidad debe verificarse en la sesión o entorno actual, limitarse al alcance aprobado y producir evidencia cuando modifica una fuente externa.

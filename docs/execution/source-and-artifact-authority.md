# Autoridad de fuentes, artefactos y entornos

IA-DOS no presupone una topología concreta de carpetas, repositorios, servicios o herramientas. Antes de planificar o ejecutar, cada recurso real debe declarar su función y autoridad.

## Contrato mínimo

| Recurso | Rol | Autoridad para | Acceso permitido | Limitaciones |
|---|---|---|---|---|
| `[RECURSO]` | `[ROL]` | `[ÁMBITO]` | `[LECTURA / ESCRITURA / ACCIÓN]` | `[LÍMITES]` |

El recurso puede ser un repositorio, carpeta, documento, Wiki, base de datos, servicio, entorno remoto, issue, pull request, dataset u otro artefacto disponible.

## Roles frecuentes

### Método

Define cómo organizar, planificar, ejecutar, verificar y reportar. IA-DOS normalmente cumple este rol y se consulta en solo lectura durante el trabajo de otros proyectos.

### Memoria durable

Conserva decisiones aceptadas, contexto, arquitectura vigente y estado conocido. No demuestra por sí sola que algo esté implementado.

### Implementación

Demuestra el estado real del producto mediante código, configuración, migraciones, pruebas, datos o artefactos desplegados.

### Evidencia y trazabilidad

Conserva tareas, diffs, reportes, pruebas, decisiones, revisiones y estados verificables.

### Referencia

Aporta antecedentes, patrones o aprendizaje. No gobierna automáticamente el resultado actual y permanece en solo lectura salvo autorización explícita.

## Contradicciones

Cuando dos fuentes discrepan:

1. identifica el tipo de información en conflicto;
2. determina qué recurso tiene autoridad para ese ámbito;
3. no resuelvas la contradicción copiando ambas versiones;
4. registra la decisión en la fuente durable correspondiente;
5. escala al Cycle Owner o a `00` cuando exceda la autoridad del espacio actual.

## Readiness del entorno

Antes de enviar una Planning Task o Execution Task, confirma solo lo necesario:

- entorno disponible: local, remoto o combinado;
- recursos accesibles;
- fuentes faltantes;
- estado que debe preservarse;
- permisos reales;
- secretos o datos que no deben exponerse;
- acciones externas o con coste que requieren autorización.

No impongas:

- una carpeta raíz específica;
- repositorios separados;
- una Wiki independiente;
- GitHub;
- trabajo local;
- una herramienta, proveedor o stack concreto.

## Regla principal

La estructura del proyecto pertenece al proyecto. IA-DOS gobierna el contrato de autoridad, acceso, evidencia y retorno, no la topología física obligatoria.
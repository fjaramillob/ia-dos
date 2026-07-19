# Readiness del entorno y reanudación

Este contrato permite continuar proyectos activos sin reiniciar IA-DOS y evita autorizar escritura antes de comprobar dependencias indispensables.

## Continuidad

Cuando el proyecto ya está en desarrollo:

- conserva conversaciones, Cycle Owner, Cycle ID y Task ID;
- no repite onboarding, clasificación ni decisiones confirmadas;
- no vuelve a `00` salvo reorientación real;
- continúa desde el último artefacto aceptado o estado bloqueado.

## Readiness antes de ejecutar

Antes de aprobar una Execution Task, comprueba sin escritura:

- runtime y versión;
- herramienta o CLI requerida;
- servicio, daemon o contenedor operativo;
- acceso, permisos y estado que preservar;
- secretos, conectividad, recursos externos y costes.

Resultado: `LISTO | NO LISTO | DESCONOCIDO`.

Una herramienta instalada no demuestra que su servicio esté operativo.

## Environment Preflight

Úsalo cuando una dependencia indispensable no esté comprobada. Es de solo lectura, no modifica el proyecto, no instala ni inicia servicios y no abre un ciclo nuevo.

Devuelve `LISTO PARA EJECUCIÓN`, `NO LISTO` con una dependencia dominante o `DESCONOCIDO` por falta de acceso.

## Acciones sobre el entorno

Distingue:

```text
inspeccionar
≠ usar un servicio ya operativo
≠ iniciar o reiniciar un servicio
≠ configurar
≠ instalar o actualizar
```

Cada Execution Task declara por separado si autoriza consultar estado, usar, iniciar, detener, configurar e instalar.

Autorizar contenedores no autoriza por sí solo iniciar una aplicación, administrar servicios del sistema ni modificar el runtime.

## Bloqueo válido

Cuando una precondición falla durante ejecución:

1. detén la tarea;
2. devuelve un Execution Report bloqueado;
3. registra evidencia y acción mínima requerida;
4. conserva la tarea aprobada si objetivo, alcance y seguridad no cambiaron;
5. no replanifiques por defecto.

## Execution Resume

Cuando el bloqueo se resuelve sin cambiar la tarea, reanuda el mismo ciclo:

```text
Artifact Type: Execution Resume
Destination Role: Coding Agent — Execution
Expected Output: Execution Report
Forbidden Output: nueva Planning Task | replantear arquitectura | ampliar alcance
Cycle ID: [MISMO CYCLE-ID]
Task ID: [MISMO TASK-ID]
Agent Session: [SESIÓN]
```

Incluye solo condición resuelta, evidencia, verificación previa, punto de reanudación, permisos vigentes y destino del reporte.

Replanifica únicamente cuando cambian objetivo, arquitectura, alcance, autoridad, seguridad, costes o resultado verificable.

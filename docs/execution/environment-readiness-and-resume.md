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
